Copy the contents of `/dir/a` into `/dir/b`, preserving permissions/times/etc, and providing overall transfer progress and some stats at the end.

```
$ rsync --archive --info=progress2,stats /dir/a/ /dir/b
```
