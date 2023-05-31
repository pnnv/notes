Environmental Variables provide information to the shell that is required for it to operate properly. These variables control the shell's behaviour, guide access to resources.

```bash
$ printenv
```
Using the above command we can print out all of the set environmental variables.



- **SHELL**:
  `$ printenv SHELL` command gives us the shell value, lets us know what we are working with.

- **TERM**:
  Describes the type of terminal to use when running the shell.

- **USER**:
  Saves the current logged in user.

- **PWD**:
  Saves the current PWD so that you can return to it using `cd` command.

- **!**:
  saves out last command so that we can access it for a variety of reasons.
  - *`!!` command runs your previous command.*
  - *We can also run `!<string>` which will go through our bash history and re-run the last command with that string.*

- **PATH**:
  Path is going to look like a comma separated list of directories, usually in the `/bin` area.
  This is the list of places the shell will look for a binary when a user types in a command.

#### PATH

```bash
$ export PATH=$PATH:/home/dennis/bin
```
This command will set the `PATH` variable equal to the old `PATH` with `:/home/dennis/bin` appended to the end. 
Now when we run a command, if a program is not found in the first directories, it will search our user's `/bin` and attempt to run whatever is found there.

- To verify which executable is being found on your `PATH`, run the command `which` followed by the name of the command we want to run. It will print out the path to the executable which will be run.

#### Set Variables

`set` prints all shell variables. `printenv` prints all environmental variables. The difference is a question of scope.

Shell variables are only applicable for the local shell, while environmental variables are passed down to child processes
 
```bash
$ FOO="dennisIsGreat"
$ echo $FOO
   dennisIsGreat
$ set | grep FOO
$ printenv | grep FOO
```

`export` adds a variable to the environmental variable group, which means it will not be available to any child processes, as well as the local shell.

```bash
$ export FOO
$ printenv | grep FOO
$ bash
   % echo FOO
   dennisIsGreat
$ unset FOO
$ set | grep FOO
$ printenv | grep FOO
$ export - n FOO
$ printenv | grep FOO
```

These last few commands have been *bash builtins*, meaning they are a part of the bash terminal rather than our OS.

#### Set Temporary Aliases

Much like setting variables, we can set aliases for frequently used commands so that we don't have to type them all the time.

```bash
$ alias lsa=’ls -a’ $ lsa 
```

#### Set Permanent Aliases

To make all the changes we made permanent, we need to change the initialized configuration the shell will load every time it starts. This is known as the `.bashrc` file, and is located at `~` in the home directory.

`.bashrc` is part of a group of files called *dotfiles*, so named because they have a dot in front of their name which makes them "hidden" files in the Linux directory system. Dotfiles are almost always used to store configuration files in Linux

Open up your `.bashrc` and add the appropriate lines to the end of it in order to permanently alias one command and set a permanent variable.