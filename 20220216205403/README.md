# Shrink image partitions

For now, create a loopback device, resize with resize2fs and shrink partition with parted, fdisk, etc.
```bash
    sudo losetup -f -P image.img
    sudo resize2fs -p /dev/loopXpY 10G # or -M to shrink as much as possible
    # Resize with parted, sfdisk then number of blocks of new image
    sudo e2fsck -fy /dev/loopXpY # rPi image is ext2
    sudo losetup -d /dev/loopX
    truncate --size=$[(block_size+1)*512] image.img
```
    #image, #partition

