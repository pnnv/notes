#### Encoding and Obfuscation

One big step down from encryption is encoding and obfuscation. While they might look like encryption, they are really just ways of translating data into another form. 
One common example is Base64 encoding which can be used to binary into printable ASCII text.

#### Hashing

- Hashes are designed to be mathematically one way, meaning it is impossible to reverse a hash into the data that was used to create it.
- Hashing functions are algorithms that take in any data, do math on it, and output a string of some set length depending on the function, that can be assumed to be unique to whatever the input was.
- One of the more famous methods of hashing is `md5`.

```bash
$ echo "password" | md5sum  
```
This command takes string "password" and gets the md5 hash of it.

If we put `"password1"` in place of `"password"`, it can be observed that the output comes out to be completely different

> The `echo` command automatically adds the newline character after our string so the hash we get is actually for the string `"password\n"`, it doesn't matter in most of the cases but in this one it does as it completely changes the output.
> We can use `-n` flag to remove trailing newline character.

```bash
$ echo -n "password" | md5sum
```
- We can also use hashing on files and programs.
```bash
$ md5sum /bin/ls
$ md5sum /etc/passwd
```

- md5 hash is used by many developers to check the integrity of the package as the whole hash changes even if a single bit is different.

#### Salting

Salting is a technique where a computer create a unique string to place at the end of every password entered. This means that they can leave their hashes completely readable, but the attacker will have a much harder time cracking them.

```bash
$ echo "password&secretsalt1337" | md5sum
```
Here we are emulating as if the user entered their new password "password", the system added on a salt, in this case "&secretsalt1337", and then the system saves the salt and the output of the md5 hash. The original password entered will not be saved anywhere.

Next time when the user enters the password, it will be combined with the salt, hashed and the hash will be checked against the originally saved one.

##### /etc/shadow

Modern Linux versions don't store passwords in `/etc/passwd`. Instead, they have been moved to `/etc/shadow`.

```
dennis:$6$iU9KjTeD$5myyo4W7zppTOEdVUeP8/E6Kmjl7CtYYFqIIyes.fnNHy1fR0gJLb0q2KLhjAH6KrPpHZ0eJorBh.D74mq.vQ.:17952:0:99999:7:::
```

```
:$6$iU9KjTeD$5myyo4W7zppTOEdVUeP8/E6Kmjl7CtYYFqIIyes.fnNHy1fR0gJLb0q2KLhjAH6KrPpHZ0eJorBh.D74mq.vQ.:
```

- `$6`
	- This represents the hashing mechanism we are using to generate the hash from password
- `$iU9KjTeD`
	- This represents the randomly generated salt used
	- In Linux the salts are randomly generated for the user when they are created. These salts are different for each user.
- `$5myyo4W7zppTOEdVUeP8...` 
	- This is the resulting hash of the taking the user's password and the randomly generated salt

- The use of `"!"` or `"*"` in this field indicates that the account cannot be logged into using a password, and must be logged into by using a alternate method, such as an SSH key.

##### Locking or Deleting an Account

```
$ sudo usermod -L account_name
```
This will lock an account.
It will modify the /etc/shadow file to have an `"*"` in front of the password field so the account cannot be logged into.

To delete an account:

```
$ sudo userdel account_name
```
