# Backups with `dd` and `lbzip2`

Use `dd` to capture all of the partitions on a disk and more fully capture the present state of a system into a single file versus cloning a single partition or one partition at a time.

Use `lbzip2` so those backups are compressed, and the compression uses many cores so at least the backup speed scales with CPU power. Some single thread algorithms seem more spcae or power efficient, but slow down the transfer too much.

## Example

Replace `/dev/nvme0n1` with the path to the device you want to backup. `lsblk` might help.

```
$ sudo dd status=progress bs=16M if=/dev/nvme0n1 | lbzip --compress --fast > /path/to/backup.img.lbzip2
```
