# Shrink image partitions

For now, create a loopback device, resize with resize2fs and shrink partition with parted, fdisk, etc.

    sudo losetup -f -P image.img
    sudo resize2fs -M /dev/loopXpY
    # Resize with parted, sfdisk

    #image, #partition

