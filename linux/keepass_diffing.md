# keepass diffing

I sync my keepass password file with multiple machines via syncthing. Occasionally, there is a conflict. When that happens, it's helpful to be able to see the differences between two keepass files.

## keepass-diff

Previously, I used a CLI exclusive tool called (`keepass-diff`)[https://github.com/Narigo/keepass-diff]. It works fine, but it has to be compiled (rust) or ran from a docker container. The README instructions are clear.

## keepassxc-cli

I recently discovered that keepassxc, the GUI I already use for keepass, ships with a CLI tool: `keepassxc-cli`. It doesn't do diffing, but with the export feature it's easy enough to compare two keepass files.

By default, though, I need to write them to a file so diff can compare them, and then delete those files.

```
$ keepassxc-cli export --format csv ~/Sync/password-file1.kdbx > tempfile1.csv
$ keepassxc-cli export --format csv ~/Sync/password-file2.kdbx > tempfile2.csv
$ diff tempfile1.csv tempfile2.csv
$ rm tempfile1.csv tempfile2.csv
```
