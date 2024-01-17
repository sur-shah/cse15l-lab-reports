# Lab Report 1

## cd 
1. `cd` with no arguments
```
No arguments
[user@sahara ~]$ cd
[user@sahara ~]$ pwd
/home
```
The `working directory` was the `/home/` directory in this case.
When using `cd` without any arguments it will automatically take the user to the `home` directory.
There is not any error present here.

2. `cd` with Directory as an argument
```
Directory as argument
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
The `working directory` was the `/home/lecture1/` directory.
When using `cd` with an argument of a directory it will bring the user to that directory
allowing them to access files or other directories within it. There is no error present here.

3. `cd` with File as an argument
```
File as an argument
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
```
The `working directory1` was the `/home/lecture1/` directory
Here when using a file as an argument for the `cd` command, it states that a file is not a directory meaning that it is unable to access said file.
This is an `error` because the command is not able to access anything as it expects a direcotry as the argument but is presented with a file. `cd` does not accept files as inputs.


## ls
1. `ls` with no arguments
```
No arguments
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls
lecture1
```
The `working directory` was the `/home/` directory.
When using the `ls` command and not providing any arguments it lists the directories in bold and files as normal and within the working directory.
There is no error present here.

2. `ls` with directory as an argument
```
Directory as an argument
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
The `working directory` is the `/home/` directory.
When using a directory as an argument for the `ls` command, it lists the files normally and the directories within the argument directory in bold. It is very similar to using `ls` without an argument, but instead, it goes to the argument directory.
There is no error present here.

3. `ls` with file as an argument
```
File as an argument
[user@sahara ~/lecture1]$ ls Hello.java
Hello.java
```
The `working directory` is the `/home/lecture1/` directory
When using a file as an argument for the `ls` command, it prints out the name of the file that was presented in the argument. There is no error present here.

## cat
1. `cat` with no arguments
```
[user@sahara ~/lecture1]$ cat
```
The `working directory` is the `/home/lecture1/` directory.
When using the `cat` command with no arguments, the command reads from the terminal. It is expecting an argument but since there is none, it goes to the next line expecting this file.
There is no error present
2. `cat` with a directory as an argument
```
[user@sahara ~/lecture1]$ cat messages
cat: messages: Is a directory
```
The `working directory` is the `/hoome/lecture1/` directory
When using the `cat` command with a directory as an argument, it throws an error because you are inputting a directory. The `cat` command expects only files to be read.
This is an error due to this.
3. `cat` with a file as an argument.

```
[user@sahara ~/lecture1]$ cat Hello.java
import java.io.IOException;
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;

public class Hello {
  public static void main(String[] args) throws IOException {
    String content = Files.readString(Path.of(args[0]), StandardCharsets.UTF_8);    
    System.out.println(content);
  }
}[user@sahara ~/lecture1]$
```

The `working directory` is the `/home/lecture1/` directory.
When using the `cat` command with a file as an argument, it will print out all of the code of the file into the terminal. In this case, I used the `Hello.java` file and it presented all lines of code in the program.
There is no error here.




