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
