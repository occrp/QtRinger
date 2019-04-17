# Keyring format

The keyring repository MUST contain:
 - a `README` file with explanation of what this repository is;
 - a `config/` subdirectory, containing:
   - an `options` file (see: [`Options file`](#options-file));
   - a `version` file, containing the string `0.1` followed by a newline;
   - a `recipients/` subdirectory containing at least a `default` recipients file (it MAY contain more recipients files; see: [`Recipients files`](#recipients-files))
 - a `keys/` subdirectory, containing zero or more PGP-encrypted files, or subdirectories containing PGP-encrypted files; see [`Keys`](#keys))

### `options` file

Repository options are settings which are saved in the repository as a global configuration stanza for a given keyring, shared by all users with access to the repository.

Options are written using the `KEY=VALUE` syntax. All lines starting with the hash (#) character are interpreted as comments.

No, there is no more documentation of this, and also this does not seem to be currently used in any way in `keyringer`.

### Recipients files

Each recipients file MUST contain at least one recipient definition line; the file MAY contain any number of empty lines, comment lines, and recipient definition lines.

Comment lines are lines starting with `#`.
Recipient definitions start with an e-mail address in the form of `user@example.com`, followed by whitespace, followed by full key fingerprint without spaces (`0123456789ABCDEF012345678ABCDEF012345678`)

Recipient files other than `default` define encryption keys for subdirectories of the `keys/` subdirectory. So, an `example-team-one` file MUST be used as source of encryption keys for all secrets in the `keys/example-team-one/` subdirectory. For any subdirectory (like `keys/example-team-one/`), if a corresponding recipients key exists (like `example-team-one`), all secrets in that subdirectory MUST be encrypted using ONLY the keys from that corresponding recipients file.

If a corresponding recipients file does not exist, ONLY THEN keys from the `default` recipients file MAY (and MUST) be used.

In other words, `defaults` recipients file defines the default keys, which are completely overridden by (NOT composed with!) the relevant recipients files for a given directory, if such a corresponding recipients file exists.

### Keys

Encrypted secrets, or "keys", MUST be stored as PGP-encrypted `*.asc` files in the `keys/` subdirectory of the keyring repository. The `keys/` subdirectory MAY contain additional subdirectories, which in turn MAY contain additional keys and subdirectories.

## Initialized empty keyring

```
$ tree
.
├── README
├── config
│   ├── options
│   ├── recipients
│   │   └── default
│   └── version
└── keys

$ git log
commit 70e392540cb89f65b803014dd71ffe88a43b5df2 (HEAD -> master)
Author: A. User <user@example.com>
Date:   Wed Apr 17 22:49:01 2019 +0200

    Initializing

$ cat README 
Keyring repository powered by https://keyringer.pw

$ cat config/version 
0.1
$ cat config/options
$ cat config/recipients/default 
# Use entries in the form of 'john@doe.com XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'

user@example.com 0123456789ABCDEF012345678ABCDEF012345678
```

