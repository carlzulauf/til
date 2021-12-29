# On Debian

You can have it report a lot more details with `-f`, but this will give all installed package names, one per line.

```
$ dpkg-query -W -f '${Package}\n'
```

# On Arch

`Q` is to query. The second little `q` is quiet mode, so the version numbers and color/control characters aren't there. Just one package name per line. 

```
$ pacman -Qq
```
