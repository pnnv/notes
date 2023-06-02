### Polyglot Files

Here we are going to make a polyglot file that can be opened as a `.gif` or as a `.jar` by taking advantage of how OS tries to open files.
Use this link to help create the jar file [https://github.com/macagua/example.java.helloworld](https://github.com/macagua/example.java.helloworld).

Then make a hello world gifar using the information in this Stackoverflow answer. [https://security.stackexchange.com/questions/116819/beside-gifar-are-there-any-other-known-polyglot-files](https://security.stackexchange.com/questions/116819/beside-gifar-are-there-any-other-known-polyglot-files).

> Graphics Interchange Format Java Archives (GIFAR) is a malware that allows attacker to piggyback off the victim's HTTP cookies. A GIFAR is a photo that can "borrow" a victim's online credentials, possibly taking over the web user's session.
> 
> GIFAR is a Graphics Interchange Format (GIF) image file combined with a JAR file. Altered GIF files can be uploaded to Web sites that allow image hosting, and run code that runs inside that site.


#### Creating and Executing a `.jar` File in Linux Terminal
[Source]()

JAR (Java Archive). It is like a zip file but for java classes. It combines all the `.class` files into a single .jar file. It is used to download all java classes on HTTP in a single operation.

1. Start by writing a simple java class with a main method for an application.
```bash
$ vim Hello.java
```
2. Compile the `.java` file to get `Hello.class`.
3. Make a file called `Manifest.mf`.
```bash
$ vim Manifest.mf
```
Inside `Manifest.mf` include:
```
Main-Class: Hello
```
Save the file.

4. Make a `.jar` using the following command.

```bash
$ jar cvmf Manifest.mf Hello.jar Hello.class
```
Now we have our jar file, we can run it using:

```bash
$ java -jar Hello.jar
```

6. Now we can merge it to a `.gif` file using:

```bash
$ cat foo.gif Hello.jar > foo.gifar
```

