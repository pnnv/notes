Related: [[Metadata]], [[File Recovery]], [[Filesystem Hierarchy]]

-----

The Linux filesystem is in a standard hierarchical setup. There are a few different file systems, but the majority use a filesystem named *ext4*.

There can be multiple filesystems on a single OS, we can use the command below to see all the filesystems hooked up to our computer:

```bash
$ df
```

`df` has a ton of output but we can ignore most of it. What we are looking for is our primary drive which is almost certainly the largest.

Filesystems are split up into blocks for ease of navigation, we can see the block size using:

```bash
$ sudo blockdev --getbsz /dev/DRIVENAME
```

The blocksize (in most cases) is 4096, the ext4 default.

### Drive Layout
A diagram showing how filesystem in laid out in a device:
```
[B][S][Inode List][ Data Blocks ] 
|  | 
|  +-- Super Block 
+----- Boot Area
```

Inode list:

*Inode are the pointers OSs use to give the location of a block of data*. Whether it is a file or a directory, there will be an inode associated with it.

These inodes are all stored together in a table towards the front of a filesystem on a drive. By reading the data on the table the OS is able to calculate the correct offset into the Data Blocks required to find the file. This is why inode stands for *index node*, because it helps us find where we put all of our files.

Each file has its own inode number, we can get it by using
`ls -i fileName`
This command will print the inode number for the file. We copy that number.

`debugfs` is a powerful tool for working directly with the drive. We can use this particular command to print out the information of the particular inode that we have selected.
```bash
$ sudo debugfs -R "stat <1521431>" /dev/DRIVENAME
```

Amidst the output, the block number, labelled as "Blocks:" or "Extents:" with a numeric value.
If the file is large enough we might get multiple Extents or Blocks.

With that offset number we can use the `dd` to calculate how far into the drive we need to go find our file.

```bash
$ dd if=/dev/DRIVENAME of=fileRecovered bs=4096 count=1 skip=547473
```

Going through the command in order:
- `dd` is the disc mount command
- We specify the input /dev/DRIVENAME, the drive file is located on
- We specify as the output fileRecovered, as the file name or whatever we find there
- `bs` is block size and is set to whatever --getbsz told us for the drive
- count is the number of blocks we are expecting to find
- skip tells us to skip that number of blocks into the drive to where the inode table told us our files would be.
When this command runs, it prints the contents of the we initially got our inode value for.

#### Deleting a file

When we `rm` a file the inode data that tells us what the LBA leading to the file is is zero'd out. This means that it is no longer useful to find the offset.

*Once this inode table has been zero'd out, whatever block it previously reserved is okay for the file system to put the new data in... but that does not mean that the data itself is gone.*

If we already know the offset, it is easy to retrieve the data using the same command as we did before with `dd` because it does not require to go through the inode table.
However, if we don't have the offset, there are still ways to recover a file aka [[File Recovery]].

