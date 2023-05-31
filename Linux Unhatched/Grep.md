A command with a similar use case is [[Find]].
These are mostly used with grep command.
```bash
grep OPTIONS [PATTERN] [FILE]
```

Suppose we have a file named passwd which happens to be a list of passwords.

```bash
grep sysadmin passwd
```
the above command will search for the exact words "passwd" in the file, but in a case where we don't quite know the exact keywords, that's where the [[Regular Expressions]] come into play.

### Basic Patterns

Regex patterns can be interpreted by only by certain commands.

Simplest is using only literal characters like in the following command:

```bash
grep sysadmin passwd
```
#### Anchor Characters

Anchor characters are one of the ways to narrow down the search results from grep. For example, `root` appears many times in `/etc/passwd` file:

```bash
grep 'root' passwd
root:x:0:0:root:/root:/bin/bash               
operator:x:1000:37::/root:
```
> To prevent shell from misinterpreting the patterns as special shell characters, these patterns should be protected by strong quotes, which simply means placing them in single quotes.

- The first anchor character ^ is used to ensure that a pattern appears at the beginning of the line. For example, to find all the  lines in `/etc/passwd` that start with `root` use the pattern `^root` . Note that `^` must be the *first* character in the pattern to be effective.

```bash
**sysadmin@localhost:~/Documents$** grep '^root' /etc/passwd
**root**:x:0:0:root:/root:/bin/bash
```
Next example:

```bash
cat alpha-first.txt
A is for Animal                           
B is for Bear   
C is for Cat     
D is for Dog      
E is for Elephant
F is for Flower
```
- The second anchor character $ can be used to ensure a pattern occurs at the *end* of a line.
```bash
grep 'r$' alpha-first.txt
B is for Bear
F is for Flower
```

#### Match a single character with .

```bash
**sysadmin@localhost:~/Documents$** cat red.txt
red
reef
rot
reeed
rd
rod
roof
reed
root
reel
read
```

- The period `.` character. It will match any character except for the new line character. The pattern r..f would find any line that contained the letter r followed by exactly two characters and then the letter f.

```bash
**sysadmin@localhost:~/Documents$** grep 'r..f' red.txt
**reef**
**roof**
```
```bash
**sysadmin@localhost:~/Documents$** grep 'r..d' red.txt
**reed**
**read**
```
```bash
**sysadmin@localhost:~/Documents$** grep '....' red.txt    
**reef**
**reee**d
**roof**      
**reed**
**root**
**reel**
**read**
```
#### Match a single character with []

The square brackets match a *single* character from the list or range of possible characters contained within the brackets.

```bash
**sysadmin@localhost:~/Documents$** cat profile.txt
Hello my name is Joe.
I am 37 years old.
3121991
My favorite food is avocados.
I have 2 dogs.
123456789101112
```
- To find all the lines in `profile.txt` which have a number in them, use pattern [0123456789] or [0-9]:

```bash
**sysadmin@localhost:~/Documents$** grep '[0-9]' profile.txt
I am **37** years old.
**3121991**
I have **2** dogs.
**123456789101112**
```

- On the other hand, to find all the lines which contain any non-numeric characters, insert a ^ as the first character inside the brackets. This character *negates* the character listed.

```bash
**sysadmin@localhost:~/Documents$** grep '[^0-9]' profile.txt
**Hello my name is Joe.**
**I am** 37 **years old.**
**My favorite food is avocados.**
**I have** 2 **dogs.**
```

> [ ^0-9 ] will not match the lines which *do not* contain numbers. It actually matches lines which contain *non-numbers* . Therefore the lines which exclusively contain numbers won't be matched.

- When other regular expressions are places inside the square brackets, they are treated as literal characters. For example, the `.` normally matches any one character, but placed inside the square brackets, then it will just match itself. In the next example, only lines which contain the `.` character are matched.

```bash
**sysadmin@localhost:~/Documents$** grep '[.]' profile.txt
Hello my name is Joe**.**
I am 37 years old**.**
My favorite food is avocados**.**
I have 2 dogs**.**
```

#### Match a repeated character or patterns with *

The regular expression `*` is used to match zero or more occurrences of a character or pattern preceding it.

```bash
**sysadmin@localhost:~/Documents$** cat red.txt
red
reef
rot
reeed
rd
rod
roof
reed
root
reel
read
**sysadmin@localhost:~/Documents$** grep 're*d' red.txt
**red**
**reeed**
**rd**
**reed**
```

It is also possible to match zero or more occurrences of a list of characters by utilising square brackets. The pattern `[oe]*` used in the following example will match zero or more occurrences of the character o *or* the e character.

```bash
**sysadmin@localhost:~/Documents$** grep 'r[oe]*d' red.txt
**red**
**reeed**
**rd**
**rod**
**reed**
```

> `o` can match *zero* occurrences of the character preceding it, therefore if it is used with just a single character, it will match all the words of the file `red.txt`.

The results in the above case can be refined by adding another `e` .

```bash
**sysadmin@localhost:~/Documents$** grep 'ee*' red.txt
r**e**d
r**ee**f
r**eee**d
r**ee**d
r**ee**l
r**e**ad
```

### Standard input

If a file is not given, the `grep` command will read from stdio, which normally comes from the keyboard with input provided by the user who runs the command. This provides an interactive experience with `grep` where the user types in the input and `grep` filters as it goes.

----

#### Extras

```bash
cat animals | grep "dog"
```

```bash
grep "dog" animals
```

both the above commands do the same thing

```bash
grep "dog" *
```

As a note, you can also `cat *` in case you ever want to print every file in a directory. Many other commands use the wildcard operator.

If you only want to know which files in a directory have the target word, use "-l".

```bash
grep -l "dog" *
```

If you want to know the file name and line number, use "-n".

```bash
grep -n "dog" *
```

If you only want to see the lines in the file which don't have the term you are greping for, use "-v".

```bash
grep -v "dog" animals
```

This defaults to showing line numbers and file names, so if you only want to see the filenames, use "-l".

```bash
grep -l "dog" animals
```

