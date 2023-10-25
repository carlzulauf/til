Sync the contents of `/dir/a` into `/dir/b`, preserving permissions/times/etc, and providing overall transfer progress and some stats at the end.

```
$ rsync --archive --info=progress2,stats /dir/a/ /dir/b
```

Do the same as above, but compress as we go.

```
$ rsync --archive --compress --info=progress2,stats /dir/a/ /dir/b
```

When we delete files from `/dir/a` and want those deletions propagated to `/dir/b` on subsequent rsyncs, do this:

```
$ rsync --archive --delete --info=progress2,stats /dir/a/ /dir/b
```
