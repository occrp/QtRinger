# Spec for QtRinger

QtRinger is a GUI for Keyringer (https://keyringer.pw/ ).

## Assumptions

 - we can use ~/.keyringer/config to map between keyring aliases and paths
 - we can write (append only or parsing and rewriting) to the keyringer config


## Features

 - create empty keyring
 - with or without a Git remote (can be added later)
 - edit keyring preferences
 - add/edit remotes
 - set default signing key (~/.keyringer/<KEYRING_ALIAS>)
 - represent secrets in a tree structure
 - allow for adding/editing/removing secrets
 - [TBD] autocommit?
 - [TBC] auto pull on startup (enabled in QtRinger settings)
 - push/pull to remotes on request (interface button)
 - [TBD] how do we handle Git?
   - eg. trying to push when remote is ahead of us
     - do we assume we're dealing with powerusers mostly and present an embedded console?
       - why not just start local terminal
       - later we should ask for confirmation before opening the console window myb? (#ux)
 - copy secret (its first line if multiline) to clipboard/selection buffer
 - move secrets between tree branches
 - ability to recrypt entries/subtrees/entirety
 - recipient group editing interface
   - possibly integrated with GnuPG keyring for easy group edits


## Repo format documentation
https://git.occrp.org/libre/qtringer/blob/master/KeyringFormat.md

## Keyringer commands

append / append-batch
check
clip / xclip
commands
commit
cp
decrypt
del / delete / rm
destroy / teardown
edit / open
encrypt / encrypt-batch
find
genkeys / genpair
git
help / usage
ls
mkdir
mv
options
preferences
pwgen
recipients
recrypt
rmdir
sclip
shell
tree
