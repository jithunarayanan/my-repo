### Resizing an ext3/ext4 file system
As a system administrator, you can resize an ext3/ext4 file systems using the `resize2fs` utility. The `resize2fs` 
utility reads the size in units of file system block size, unless a suffix indicating a specific unit is used. 
The following suffixes indicate specific units:

- s (sectors) - `512` byte sectors
- K (kilobytes) - `1,024` bytes
- M (megabytes) - `1,048,576` bytes
- G (gigabytes) - `1,073,741,824` bytes
- T (terabytes) - `1,099,511,627,776` bytes

**Prerequisites**

- An ext3/ext4 file system.
- An underlying block device of an appropriate size to hold the file system after resizing.

**Procedure**

To resize an ext3/ext4 file system, take the following steps:

- To shrink and grow the size of an unmounted ext3 file system:
```
# umount /dev/block_device
# e2fsck -f /dev/block_device
# resize2fs /dev/block_device size
```
Replace */dev/block_device* with the path to the block device, for example ```/dev/sdb1```.

Replace size with the required resize value using `s`,` K`, `M`, `G,` and` T` suffixes.

An ext3/ext4 file system may be grown while mounted using the `resize2fs` command:
```
# resize2fs /mount/device size
```
>**Note:**
The size parameter is optional (and often redundant) when expanding. The `resize2fs` automatically expands to fill 
the available space of the container, usually a logical volume or partition.

To view the resized file system:
```
# df -h
```
