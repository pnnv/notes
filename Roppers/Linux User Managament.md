Users are differentiated and monitored by the OS according to User ID (UID). Groups are identified using (GID). When we open a file or a directory, the permissions are checked against our UID and GID. If all checks out, we are given access.

##### /etc/passwd

While usernames are used in human-visible interface for computing, behind the scenes, the OS operates using UIDs. As different operations occur, the OS checks these UIDs against a file that is represented in the Linux filesystem as `/etc/passwd`. All of the files can not only be viewed, but can be edited if we have the appropriate permissions.

To view:
```bash
$ cat /etc/passwd
```

Here we will see a printout of all the users with accounts on the computer. The top one will be 'root', and will look generally like this.

```
root:x:0:0:root:/root:/bin/bash dennis:x:1337:1337:Dennis:/home/dennis:/bin/bash
```


/etc/passwd stores data about users separated by colons.

1. User name
2. Encrypted password
	- On modern systems, the password will not be stored here and is indicated by an 'x',
3. User ID number (UID)
4. User's group ID number (GID)
5. User's full name and other data (GECOS)
	- The is an arbitrary set of data also known as the "comment" field. Sometimes name, email, phone number, separated by commas. Most of the times there is nothing here but out name.
6. User home directory
7. Default login shell


##### /etc/group

Similar to `/etc/passwd`, this prints out information about various groups on the computer.

```
sys:x:3:bin,pranav
wheel:x:998:pranav
rfkill:x:982:pranav
pranav:x:1000:
```
1. Group name
2. Group password - Using an elevated privilege like sudo is standard, but a separate password can be added. `"*"` will be put in place as the default value.
3. Group ID (GID)
4. List of users - Manually specified users in the group

##### Adding a user and setting a password

```bash
$ sudo useradd -c "User's Full Name" account_name
$ sudo passwd account_name
```

##### Deleting an account
```bash
$ userdel -r account_name
```

`userdel` with the `-r` flag is final and will delete the user along with their home directory.

##### Set passwords
```bash
$ passwd -S account_name
```

Ex:
```bash
$ sudo passwd -n 1 -x 120 -w 4 -i 10 dennis
```

- `-n 1`: This flag sets the minimum number of days before the password changes.
- `-x 120`: This flag sets maximum number of days before the password expires.
- `-w 4`: This flag specifies the number of days before a password is about to expire when the user should start receiving warning messages.
- `-i 10`: This flag sets the number of days after the password expires before the account is locked.
- `dennis` is the username for which the settings will be modified.

Other flags:

- `-a` or `--all`: This flag is used to update password for all the users in the system.
- `-d` or `--delete`: This flag is used to delete password for a user account.
- `-e` or `--expire`: This flag is used to force the expiration of a user's password.
- `-l` or `--lock`: This flag is used to lock a user's password. Once the password is locked, the user won't be able to log in with that account until it is unlocked.
- `-u` or `--unlock`: This flag is used to unlock a previously locked account
- `-S` or `--status`: This flag is used to display the status of a user account, specifically password related information.
- `-r` or `--repository`: This flag is used to specify an alternative password repository or directory. It is commonly used in systems with centralized user authentication systems.