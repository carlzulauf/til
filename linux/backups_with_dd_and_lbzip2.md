# Backups with `dd` and `lbzip2`

Use `dd` to capture all of the partitions on a disk and more fully capture the present state of a system into a single file versus cloning a single partition or one partition at a time.

Use `lbzip2` so those backups are compressed, and the compression uses many cores so at least the backup speed scales with CPU power. Some single thread algorithms seem more spcae or power efficient, but slow down the transfer too much.

## Example

Replace `/dev/nvme0n1` with the path to the device you want to backup. `lsblk` might help.

```
sudo dd status=progress bs=16M if=/dev/nvme0n1 | lbzip2 --compress --fast > /path/to/backup.img.lbzip2
```

### Restoring From File to Device

Pipe decompressed image into dd and out to your device.

```
lbzip2 --decompress --stdout /path/to/backup.img.lbzip2 | sudo dd status=progress bs=16M of=/dev/nvme0n1
```

## Split by max file size

If you're backing up disks you might be backing up to multiple media or to a filesystem with file size limits. Here is how to make a new file every 2GiB.

```
sudo dd status=progress bs=16M if=/dev/nvme0n1 | lbzip2 --compress --fast | split --bytes=2G - /path/to/backup.img.lbzip2-
```
In this example if the device contains more than 2G of compressed data you'd have multiple files in `/path/to` with each file beginning with `backup.img.lbzip2.` followed by a hex id.

### Restore From Many Files to Device

You can still go from a bunch of files straight to the target device.

```
cat /path/to/backup.img.lbzip2.* | lbzip2 --decompress --stdout | sudo dd status=progress bs=16M of=/dev/nvme0n1
```
