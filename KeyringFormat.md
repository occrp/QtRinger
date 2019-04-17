# Keyring format

The keyring repository MUST contain:
 - a `README` file with explanation of what this repository is;
 - a `config/` subdirectory, containing:
   - an `options` file (see: [`Options file`](#options-file));
   - a `version` file, containing the string `0.1` followed by a newline;
   - a `recipients/` subdirectory containing at least a `default` recipients file (it MAY contain more recipients files; see [#recipients-files](#recipients-files))

### `options` file

### Recipients files

Each recipients file MUST contain at least one recipient definition line; the file MAY contain any number of empty lines, comment lines, and recipient definition lines.

Comment lines are lines starting with `#`.
Recipient definitions start with an e-mail address in the form of `user@example.com`, followed by whitespace, followed by full key fingerprint without spaces (`0123456789ABCDEF012345678ABCDEF012345678`)

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

