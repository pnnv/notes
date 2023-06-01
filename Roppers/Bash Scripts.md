Bash has a built in scripting language. These days we can use Python for most things instead of writing Bash scripts.

- Bash scripts use `.sh` extension.
- Every bash script has the top line which tells the shell what type of script it is:
```bash
#!/bin/bash
echo "Hello World"
```
- Then we can execute it using command `$ bash hello.sh`, similarly we can make the file executable and execute it using `$ ./hello.sh`.

```bash
#!/bin/bash
echo "Enter your name"
read name
# read is a bash builtin function that isn't available in the shell

date="$(date)"
# We just set the value that date returns to date using
# "command substitution"

echo "Welcome $name it is $date"
```

Ex 2: Here is a bash script that counts to 10

```bash
#!/bin/bash
valid=true
count=1
while[$valid]
do
echo $count
if[$count -eq 10];
then
break
fi
((count++))
done
```

#### Cron Jobs

A crontab file contains instructions for the cron daemon in the following simplified manner: *run this command at this time on this date*. Each user can define their own crontab file. Commands defined in any given crontab are executed under the user who owns that particular crontab.

To see what is in out crontab file, run `crontab -l`. To edit it, run `crontab -e`.

Add this to the bottom of cronjobs to execute `counter.sh` script every minute.
`*/1 * * * * /home/studentName/Documents/counter.sh`

# More from THM

- We can perform normal Linux commands inside out bash scripts and it will be executed if formatted right

**Variables**:

In bash variables can be created follows
```bash
name="Pranav"
```
Where we give the value of `Pranav` and assign it to `name`.
*Note that we can't leave a space between the variable name, the "=" and the variable value*. They cannot have spaces in.

To use variables we put a `$` in front of them. 
```bash
echo $name
```

**Debugging**:

Bash has a built in method for debugging.
While running at the command line we can do:
```bash
bash -x /.file.sh
```
This tells us which lines are working and which are not.

- If we want to debug a certain portion of the script, we can insert `set -x` at the beginning and `set +x` at the end of that portion.
```bash
#!/bin/bash
echo "hi"
set -x

#this section will be debugged

set +x
```

**Parameters**:

Parameters are one of the main features of bash.
- Parameters often have "$" prefix because parameter is still a variable.

In the following script, we take as parameter out first argument and use it.

```bash
#!/bin/bash
name=$1

echo $name
```

We now run our script with `./example.sh Pranav` and sure enough we get returned with `Pranav`

Similarly to get the second argument, we can add a `$2` and so on.

As seen above, we can also prompt the user for name.

```bash
#!/bin/bash
echo "Enter your name"
read name
echo "Hello $name"
```

We can get the number of arguments supplied to the script using `$#`.

**Arrays**:

Arrays are used to store multiple pieces of data in one variable, which can be extracted by using an index

The syntax for array in bash is as follows.
```bash
#!/bin/bash

transport=('car' 'train' 'bike' 'bus')
# we can echo out all the elements in out array like this:
echo "${transport[@]}"
```
Where `@` means all arguments, and the `[]` wrapped around it specifies the index. 

`unset transport[1]` removes the `train` item.

**Conditionals**:

Conditionals mean certain pieces of code that rely on a condition being met

We will make a simple `if` statement to check if a variable is equal to a value, we will also make a script that checks if a file exists and that it is writable, if it is we will write a message to that file, if it isn't we will delete that file and make a new one.

All if statements look like:

```bash
#!/bin/bash

if [some condition]
then
	something
else 
	something different
fi
```

```bash
#!/bin/bash
count=10

if[$count -eq 10]
then
	echo "true"
else
	echo "false"
fi
```

- The `-eq` is one way of doing it, we could also use `=`

 operator | description 
---|---
`-eq` | checks if the value of two operands are equal or not; if yes, then the condition becomes true
`-ne` | same as `-eq` but returns true if the values are *not equal*
`-gt` | checks if the value of left operand is greater than the value of right operand; if yes, then the condition becomes true
`-lt` | opposite of `-gt`
`-ge` | checks if the value of left operand is greater then or equal to the left operand; if yes, then the condition becomes true

```bash
#!/bin/bash

value="guessme"
guess=$1

if ["$value" = "$guess"]
then
	echo "They are equal"
else
	echo "They are not equal"
fi
```

If we run this in our terminal.

```
$ ./example.sh guessme
They are equal

$ ./example.sh hi
They are not equal
```

For the next example:

```bash
#!/bin/bash

filename=$1

if [ -f "$filename" ] && [ -w "$filename" ]
then
	echo "hello" > $filename
else
	touch "$filename"
	echo "hello" > $filename
fi
```

- The `-f` checked if the file existed
- The `-w` checked if the file was writable, without write permissions we wouldn't be able to output our text into the file

