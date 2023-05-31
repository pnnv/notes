- Running a command results in something called a *process*. 
The `ps` command can be used to list processes.

```bash
ps [OPTIONS]
```
```bash
**sysadmin@localhost:~$** ps
  PID TTY          TIME CMD
   80 pts/0        00:00:00 bash
   94 pts/0        00:00:00 ps
```

- PID: The process identifier, which is unique to the process. This information is useful for controlling the process by ID number.
- TTY: The name of the terminal where the process is running. This information is useful for distinguishing between different processes that have the same name.
- TIME: The total amount of processor time used by the process.
- CMD: The command that started the process.

> Instead of just showing the processes running in the terminal `-e` option can be used which displays every process.

```bash
**sysadmin@localhost:~$** ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD                             
root         1     0  0 19:16 pts/0        00:00:00 /sbin??? /init                  
syslog      33     1  0 19:16 ?            00:00:00 /usr/sbin/rsyslogd              
root        37     1  0 19:16 ?            00:00:00 /usr/sbin/cron                  
root        39     1  0 19:16 ?            00:00:00 /usr/sbin/sshd                  
bind        56     1  0 19:16 ?            00:00:00 /usr/sbin/named -u bind         
root        69     1  0 19:16 pts/0        00:00:00 /bin/login -f                   
sysadmin    79    69  0 19:16 pts/0        00:00:00 -bash                           
sysadmin    95    79  0 19:43 pts/0        00:00:00 ps -ef
```

