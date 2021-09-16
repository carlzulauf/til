I often do disk level copies to backup drives using `dd`. This utility can read/write pretty close to as fast as the drive allows.

Passing the output of `dd` to a compressor like `gzip` slows this down considerably and the bottleneck becomes the single core compression speed. The `--fast` option helps a little, but very little.

There are multi-threaded compression tools, though, and using these on a modern many-core CPU pretty much erases the bottleneck (if I don't mind my CPU screaming). `lbzip2` seems like one of the fastest, and since I'm mostly interested in making sure the free space gets compressed the quality of the compression isn't something I care much about, though this is said to be competitive. For some reason, probably batch size, the `--best` option is actually faster than the `--fast` option on my Ryzen 7 3700X desktop when `dd` is streaming from an SSD.

```
sudo dd if=/dev/sda2 | lbzip2 -z > /backups/sda2.iso.bz2
```
