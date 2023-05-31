It is always recommended to take backup or snapshot while before playing around with hard disc stuff.

#### Expanding Partition

There are a lot of ways to expand partition, most of which involve `gparted`.

For simpler stuff, we can just use a sequence of commands.

1. Use `df -h` to find the name of the partition. Look for one that is the largest.
2. enter the command `cfdisk`.
3. Choose the partition to extend and select "Resize".
4. Set the "New size", filling up the rest of the available area.
5. After pressing enter, you'll see screen with the following note "Partition [some number] resized".
6. Next you'll need to "Write" to save your changes. Type "yes".
7. Quit `cfdisk`. When you exit you may see the message "syncing disks", but either way good things are happening.
8. Get filesystem name again for next step with `df -h`. Nothing should have changed yet.

Now using the name you found for the filesystem, run the following command with `resize2fs`. This command will automatically match the size of the partition to the size of available disc space.

```bash
$ resize2fs /dev/nameOfFilesystem 
resize2fs 1.42.13 (17-May-2015) Filesystem at /dev/nameOfFilesystem is mounted on /; 
on-line resizing required old_desc_blocks = 1, new_desc_blocks = 2 
```
8. Then verify everything worked using `df -h` again to see size change.

