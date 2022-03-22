`lbzip2` uses all the cores. I want to make tar archives with it. Here is one way.

```
$ tar cv a_project | lbzip2 -z > a_project.tar.bz2
```
