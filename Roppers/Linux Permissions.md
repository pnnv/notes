After running `ls -l` on a directory, results look something like this:

```
drwxr-x--- 2 username groupname 4096 Jan 21 14:02 folder1
-rwxr-x--- 1 username groupname 15 Jan 21 14:02 file2
```

- The first bit tells us what type of file it is
	- "d" means directory 
	- "-" means normal file
	- There are more options that can go there, but these are most of them.
- The next 9 bits are permission bits
	- We'll be learning about those in this part
- The next bit, a number, tells us how many hard links there are to the file.
- The first name is the username who owns the file.
- The second name is the group who owns the file. Unless there is a group set up, this also shows username.
- The next number is file size in bytes
	- Directories are always the same size, but individual files should be listed as the number of bytes that make them up.
- The next numbers should be the date and time last modified. These are not forensically accurate but are good enough to sort by timestamp.
- Finally, the name of the file you are looking the details of.

*The nine bits are split into three triplets that represent the permissions for "User", "Group" and "Other".*

These triplets are comprised of 'r', 'w', and 'x', which stands for read, write, and execute. The lack of permission to do the actions is represented by '-'.

#### Modifying Permissions

We can use `chmod` with either "u" (for user), "g" (for group), "o" (for others), or "a" (for all three) to do this on Linux. It's fairly straightforward, we either add ("+") or remove 
("-") permissions with "r", "w", and "x". Here are some examples:

```bash
$ chmod g+x file2 
>I bet you can guess what that does: 
>add the executable bit to the group permission for file2. 
> Run ```ls -l``` again and you will see it has changed. 
$ chmod g-w directory2 
>Now we have removed the write bit for a directory2 for group. 
$ chmod a+x file2 
>Now we have added the executable bit for everyone.
```
We can use `chmod` to modify any permission on the file we own, as long as we have the permission to modify permissions. 

The most common use of `chmod` is when we download a file from somewhere, it is not given the "x" privileges by default due to security policy.

If we want to change permissions of something we don't own, we are going to need root access for that.

```bash
$ sudo chown root file2
```

Similar to `chown` is `chgrp` which changes the group. Basically the same usage as `chown`.

-----

A final thing we can do is set something known as "the sticky bit".

```bash
$ chmod +t file2
$ chmod +t directory2
```

This "+t" sets the file or directory as non-deletable by anyone other than the owner and the root. This is great for shared folders.

#### Bits and Permissions


If we have three bits, those bits can range from "111" to "000" which represents 7-0. This allows us to represent permissions as numbers as well.
- The read bit is "4"
- The write bit is "2"
- The execute bit is "1"

This allows us to set permissions in a much cooler way.
`$ chmod 755 file2`

We can also remove permissions by using lower numbers.
`$ chmod 744 file2`

We just removed the execute bit for group and others.

-----

When a file is created in Linux, the default permissions for it is "666". For a directory the default permissions are "777".
*We can modify the default permissions using a command named `umask`*

#### Masks

- Masks are generally defined as strings of bits that set other bits based on logic. The logic is based on digital logic gates.
- One of the more common uses of masks we see in Linux is for controlling default permissions.

```
EX. 1

Binary  6 6 6 // 110 110 110
Mask:   0 2 2 // 000 010 010
Output: 6 4 4 // 110 100 100
```

```
EX. 2

Binary  7 7 7 // 111 111 111
Mask:   0 4 2 // 000 100 001
Output: 7 3 5 // 111 011 110 
```

- Masks aren't used a lot but are good to know about.

- To find what the default mask is for out OS we can use the `umask` command.
- In order to change our permissions that the files default to we can use: `$ umask 002`
  
  This `umask` of "002" converts over to being a mask of "775".
  
  When applied this will change permissions so that files come out `rwx` for user and group and `r` for other.