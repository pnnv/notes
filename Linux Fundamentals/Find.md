`find` command is similar to [[Grep]] but while `grep` cares about the contents of the file, `find` only cares about the name name of the file and its information.

```bash
$ find directoryName -name nameOfFile
>finds all the files with the given name

$ find dirName -type f -name "*.txt"
>find all .txt files.

$ find dirName -type f -perm 0777 -print
>finds all the files with permission 0777

$ find / -user pranav
>finds all the files owned by pranav (starting from the root)

$ find / -size 50M
>self explanatory

$ find / -mtime 5
>find all files modified in last 5 days

```

Kind of useful for forensics standpoint, though timestamps tend to be a bit unreliable.

