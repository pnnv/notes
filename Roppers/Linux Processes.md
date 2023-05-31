Anytime we run a command we run in the shell, as well as the shell itself, as well as the programs run by the OS, a process is created. Each of these processes runs in memory on the CPU.

#### `ps` & `top`

The most common way to view processes is by running the `ps` command.

```bash
$ ps -u <username>
```

 This will return the results in the format:
```
PID TTY          TIME CMD  
954 tty2     00:00:28 Web Content 
1262 pts/1    00:00:00 ps 
7020 ?        00:08:38 evince ... and many more
```
- `PID` stands for process ID, and is the unique identifier associated with a specific process. They generally increment as a new process is started.
- `TTY` stands for TeleTYpewriter, which tells us the file name of the terminal connected to standard input. 
  Here we can see `tty2`, which tells us second terminal.
  We can also see `pts/2` for the `TTY` that ran the `ps` command. `pts` stands for "pseudo terminal slave" and generally is a tab or SSH connection to a terminal.

The more common way the `ps` command is used is:
```bash
$ ps aux
```
This returns all the data about all the processes in the computer.

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND 

root         1  0.0  0.1 173320 16324 ?        Ss   Mar22   2:28 /usr/lib/systemd/systemd 

student  32529  0.0  0.0 226464  5352 pts/7    Ss+  Mar30   0:00 bash 

root     30555  0.0  0.0 257044 10092 pts/3    S+   10:16   0:00 sudo wireshark 

avahi      975  0.0  0.0  32136  5440 ?        Ss   Mar22   1:08 avahi-daemon: running 
```

Now, we also have some new options:

- `USER` shows who owns each process, some users are made specifically to run a process. These processes are called *daemons* and can be defined as a computer program that runs as a background process, rather being under the direct control of an interactive user.
  
  We can see that `avahi-daemon` process run by the `avahi` user. A second daemon (traditionally indicated by a trailing "d" in the name) we can see is `systemd`, which has `PID` of 1.

- `PID` of 1 tells us that `systemd` is the init process, or initialization process that all the processes on the system were spawned from.

- Other options visible are `%CPU` and `%MEM`, which tells us exactly how much resources are being used by every process.

- `VSZ` is the virtual memory size and tells us how much memory is allocated to the process. 

- `RSS` is the Resident Set Size and is used to show how much memory for that process is in RAM.

> There is an important distinction between swap space and virtual memory.

- Again we have `TTY` and then `STAT`, which tells us the current status of the process.

- `START` gives us the starting time of the process, or the date if it has run for over 24 hours.

- `TIME` gives us the total CPU time the process has been running.

- `COMMAND` gives us the extended version of `CMD`, with the path and all the arguments the process was executed with.

If we only want to look for a single type of process, we can `grep` for it using a pipe.
>Time to revisit [[Grep]].  

```bash
$ ps aux | grep bash
```

If we only care about who is using most resources, we can use `top` command.

```bash
$ top
```

#### Killing Processes

If we have the PID, we can simply type `kill` followed by the PID. `top` or `ps | grep` are great for finding those PIDs.

```bash
$ kill 1234
```

If we want to kill all processes with a certain name, `pkill` is very useful.

```bash
$ pkill nc
```

#### Types of processes

```bash
$ ps -ef
```
Running this, we see a similar result but with an extra column named `PPID`, or "Parent Process ID". This is the parent process that spawned the process listed.

Even better way of visualizing this is:
```bash
$  ps -e -o pid,args --forest
```

```
23453  \_ /usr/libexec/gnome-terminal-server 
 5868  |   \_ bash 
26785  |   |   \_ ps -e -o pid,args --forest 
22769  |   \_ bash 
22812  |   \_ bash
```
This shows the processes in a nice, tree-like format, we can even see the command we ran along with the arguments we passed.

- When a child process is started, the OS keeps track of it and associates it with the parent.

- When the child process exits, completion is reported to the parent and the process is "reaped" from the process list.

- Orphan process are the process whose parent process completed execution or was killed prior to the child process completing.
  The OS keeps track of the parent and child relationships and informs a parent when their child has died but does not inform a child when their parent has died, and it just continues to run as normal.

- When an orphan process completes, the OS sees that the parent process is dead and will "reap" the orphaned process itself with systemd, the init daemon with PID 1.

- When when a child process is completed or exited, the process table is updated to reflect new status.

> If a parent process does not check the process table to receive a notification in a timely fashion, the finished child cannot be reaped. As long as the parent process is alive the OS will not step in.

This is referred to as *zombie process*.

#### Backgrounding

First, let's run `nc -l 1338` in a terminal window, and open a new window.

Next run this command in the new window `nc -l 1337 &` to setup a netcat listener that "backgrounds" itself and returns control of the terminal to us.

```
student  27347 0.0  0.0   8172  2184 pts/3    S+   11:06   0:00 nc -l 1338 
student  27389 0.0  0.0   8172  2188 pts/3    S    11:03   0:00 nc -l 1337
```

Besides PID and the command issued, a notable difference is that the `STAT` column shows S and S+. 

Here are the different values that the s, stat and state output specifiers (header "STAT" or "S") will display to describe the state of a process:

- D uninterruptible sleep (usually IO)
- I Idle kernel thread
- R running or runnable (on run queue)
- S interruptible sleep (waiting for an event to complete)
- T stopped by job control signal
- t stopped by the debugger during tracing
- W paging (not valid since 2.6.xx kernel)
- X dead (should never be seen)
- Z defunct ("zombie") process, terminated but not reaped by its parent

For BSD formats and when the stat keyword is used, additional characters may be displayed:

- < high-priority (not nice to other users)
- N low-priority (nice to other users)
- L has pages locked into memory (for real-time and custom IO)
- s is a session leader
- l is multi threaded (using CLONE_THREAD, like NPTL threads do)
- + is in the foreground process group

Using the command `jobs` we can see what backgrounded processes are running. Interestingly, if we run `jobs` in a different tab than where we ran the backgrounded listener, nothing will pop up. This is because they are in a different parent process, so `jobs` won't find them (Remember, computers are not magic). Once we navigate to the tab we ran the backgrounded process in we can use the `fg` command to bring them forward. With no args `fg` will take the first item, otherwise we can specify with ``fg `%<job #>``.

#### Signals

Signals are a part of something called "Interprocess communication". Interprocess communication is the mechanism the OS provides so that processes are able to work with each other.

Signals are notifications to a process that an event has occurred.
The most common signals are the ones used to kill processes when we use `kill` or `pkill` commands, along with closing browser tabs and terminal windows at the lowest level.

Run the command `nc -l 1337` and then press Ctrl-z.

Ctrl-z sends a signal to the OS which modifies the process and automatically stops the process' execution. Notably, it does not background the process we can do that with `bg` command and bring it to foreground using `fg` command.

Once the process is brought to the foreground, pressing Ctrl-c sends another signal and causes the process to receive an "interrupt" signal. This will kill the vast majority of the process and is a great way of killing hanging processes.

> There are also things called "interrupts" and "exceptions" that are similar to signals, but instead of being generated by OS, they are actually generated by the underlying hardware, usually when a fault occurs.


#### proc

- The command `ps` does not find all that information for us, but instead, it is reading a series of text files that the Linux kernel provides.

- We can `ls /proc` and by looking at different files within, we can find all sorts of information.

- The directories in `/proc` don't exist until they are asked to.