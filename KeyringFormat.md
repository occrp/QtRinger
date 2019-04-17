# Keyring format

Initialized empty keyring:

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

$ cat config/version 
0.1
$ cat config/options
$ cat config/recipients/default 
# Use entries in the form of 'john@doe.com XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'

user@example.com 0123456789ABCDEF012345678ABCDEF012345678
```

