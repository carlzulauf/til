# partclone

Clone partitions from block devices without cloning the empty blocks. Uses it's own image format to makes smaller images.

## Install

### Arch

```
sudo pacman -S partclone
```

## Backup a btrfs partition to a compressed file using lbzip2

```
sudo partclone.btrfs -c -x lbzip2 -s /dev/sda2 -o /run/media/manjaro/backup/shared/sda2.img.bz2
```
