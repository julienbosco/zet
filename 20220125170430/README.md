# Repartition a USB Drive

    gdisk /dev/sda # o to create new GPT, n to create new partition, w to write to disk
    mkfs.vfat -F 32 -n VOLUME_NAME /dev/sda1


    #usb #partition
