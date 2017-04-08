#### Usb Key installation won't boot (Os not found) 

This happens if you have a newer version of Linux, trying to boot on Legacy menu instead of UEFI and your BIOS doesn't recognize partitions without the boot flag.

The solution is as simple as adding the boot flag on the ext4 partition, here's how I did it for Manjaro.

Run this on Terminal:

`parted -l`

Will list all the partitions.

Check if the ext4 of the USB you want to boot has the boot flag.
Some BIOS need it to be able to run.

```
Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdd: 62.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  53.2GB  53.2GB  primary  ext4            
 2      53.2GB  62.1GB  8907MB  primary  linux-swap(v1)
```

So in this case, we want to update /dev/ssd and the partition 1 to enable flag boot.

We do this then:
`sudo parted /dev/sdd set 1 boot on`

This will fix the partition and it will work.