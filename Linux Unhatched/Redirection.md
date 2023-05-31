There is a way in Linux to quickly add content to a file using a command line feature called *input/output (I/O) redirection*.
I/O redirection allows for information in the command line to be sent to files, devices, and other commands.

When it comes to command input or output, there are three paths, or "tracks". These paths are called *file descriptors*. 
1. Standard Input (STDIN)
2. Standard Output (STDOUT)
3. Standard error (STDERR)

To redirect STDOUT from where we would normally see it (in the terminal) to a file we in the file system. To use redirection, simply use a > symbol along with a file name as follows:

```
[COMMAND] > [FILE]
```

```bash
echo "hello world" > hello.txt
```

> Note that doing this will replace the original content of the file(if it exists). To avoid that, i.e. to append the output to the contents of the file, use a double greater-than symbol:

>To redirect output to a file, the user must have the appropriate permissions to that file.

