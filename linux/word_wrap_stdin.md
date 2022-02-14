`fold` is a unix utility for wrapping STDIN and passing it to STDOUT.

```
$ cat file | fold # defaults to 80
$ cat file | fold -c40
$ cat file | fold -c40 -s # break on space
```
