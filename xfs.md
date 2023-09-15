### Creating an XFS file system with mkfs.xfs
This procedure describes how to create an XFS file system on a block device.

**Procedure**

To create the file system:

If the device is a regular partition, an LVM volume, an MD volume, a disk, or a similar device, use the following command:
```
# mkfs.xfs *block-device*
```
Replace block-device with the path to the block device. For example, `/dev/sdb1`, `/dev/disk/by-uuid/05e99ec8-def1-4a5e-8a9d-5945339ceb2a`, 
or `/dev/my-volgroup/my-lv`.

In general, the default options are optimal for common use.
When using `mkfs.xfs` on a block device containing an existing file system, add the `-f` option to overwrite that file system.

To create the file system on a hardware RAID device, check if the system correctly detects the stripe geometry of the device:

If the stripe geometry information is correct, no additional options are needed. Create the file system:
```
# mkfs.xfs block-device
```
If the information is incorrect, specify stripe geometry manually with the su and sw parameters of the -d option. The su parameter specifies the RAID chunk size, and the sw parameter specifies the number of data disks in the RAID device.

For example:
```
# mkfs.xfs -d su=64k,sw=4 /dev/sda3
```
Use the following command to wait for the system to register the new device node:
```
# udevadm settle
```
ADDITIONAL RESOURCES
```
mkfs.xfs(8) man page.
```


### Increasing the size of an XFS file system with xfs_growfs
This procedure describes how to grow an XFS file system using the `xfs_growfs` utility.

**Prerequisites**

- Ensure that the underlying block device is of an appropriate size to hold the resized file system later. Use the 
appropriate resizing methods for the affected block device.

- Mount the XFS file system.

**Procedure**

- While the XFS file system is mounted, use the `xfs_growfs` utility to increase its size:

```
# xfs_growfs file-system -D new-size
```

- Replace `file-system` with the mount point of the XFS file system.
- With the `-D` option, replace new-size with the desired new size of the file system specified in the number of file system blocks.

	To find out the block size in kB of a given XFS file system, use the `xfs_info` utility:

```
# xfs_info block-device

...
data     =              bsize=4096
...
```
- Without the -D option, xfs_growfs grows the file system to the maximum size supported by the underlying device.


ADDITIONAL RESOURCES
```
xfs_growfs(8) man page.
```
