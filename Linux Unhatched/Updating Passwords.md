The `passwd` command is used to update a user's password. Users can only change their own passwords, whereas the root user can update the password for every user.
```bash
passwd [OPTIONS] [USER]
```


If we simply type in `passwd` in the terminal, we are asked for the current password of the user that we are logged in to, and after that the new password (twice) that we would like to set.

If the user wants to view *status* information about their password, they can use `-S` option:

```bash
**sysadmin@localhost:~$** passwd -S sysadmin                                        
sysadmin P 12/20/2017 0 99999 7 -1
```

