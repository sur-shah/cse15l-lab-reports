# Lab Report 1

## cd 
1. `cd` with no arguments
```
No arguments
[user@sahara ~]$ cd
[user@sahara ~]$ pwd
/home
```
The `working directory` was the `home` directory in this case.
When using `cd` without any arguments it will automatically take the user to the `home` directory.

2. `cd` with Directory as an argument
```
Directory as argument
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
The __working directory__ was the __lecture1__ directory.
When using `cd` with an argument of a directory it will bring the user to that directory
allowing them to access files or other directories within it.

3. `cd` with File as an argument
```
File as an argument
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
```
The `working directory1` was the `lecture1` directory
Here when using a file as an argument for the `cd` command, it states that a file is not a directory meaning that it is unable to access said file.
This is an `error` because the command is not able to access anything as it expects a direcotry as the argument but is presented with a file.


## ls
1. `ls` with no arguments
```
No arguments
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls
lecture1
```
The `working directory` was the `home` directory.
When using the `ls` command and not providing any arguments it lists the directories in bold and files as normal and within the working directory.

2. `ls` with directory as an argument
```
Directory as an argument
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  messages  README
```
The `working directory` is the `home` directory.
When using a directory as an argument for the `ls` command, it lists the files normally and the directories within the argument directory in bold. It is very similar to using `ls` without an argument, but instead, it goes to the argument directory.

3. `ls` with file as an argument
```
File as an argument




