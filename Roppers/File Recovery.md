First we need to turn off the computer because once those blocks are freed, any process can overwrite them. By turning off the computer we can guarantee that this does not happen.

By booting into the turned off computer with a separate OS we can then mount the affected hard drives as read only. From there, we can search through the hard drive for the raw file and hope we can still find it.

Now we'll be using [[Grep]] again, this time to look up for a known pattern in the file and then take 500 bytes before and after and save it to a file named /tmp/recover, as well as displaying it on the screen.

```bash
$ grep -a -C 500 'known pattern' /dev/sda | tee /tmp/recover
```

Instead of using `grep` we can use an actual recovery tool. Just like grep for a known pattern, file recovery tools know what the file format is for files like images or videos.
Instead of looking for the offset they can just scan through the drive until they find the correct file format headers and save the rest of the file.