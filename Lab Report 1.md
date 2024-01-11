# Lab Report 1

## cd 
```
No arguments
[user@sahara ~]$ cd
[user@sahara ~]$ pwd
/home
```
The working directory was the home directory in this case.
When using cd without any arguments it will automatically take the user to the home directory.

```
Directory as argument
[user@sahara ~]$ cd lecture1
[user@sahara ~/lecture1]$ pwd
/home/lecture1
```
The working directory was the leecture1 directory.
When using cd with an argument of a directory it will bring the user to that directory
allowing them to access files or other directories within it.

```
File as an argument
[user@sahara ~/lecture1]$ cd Hello.java
bash: cd: Hello.java: Not a directory
```
The working directory was the lecture1 directory
Here when using a file as an argument for the cd command, it states that a file is not a directory meaning that it is unable to access said file.
This is an error because the command is not able to access anything as it expects a direcotry as the argument but is presented with a file.


## ls
```
No arguments
[user@sahara ~]$ pwd
/home
[user@sahara ~]$ ls
__lecture1__
```
The working directory was the home directory.
When using the ls command and not providing any arguments it lists the directories in bold and files as normal and within the working directory.

```
Directory as an argument
[user@sahara ~]$ ls lecture1
Hello.class  Hello.java  __messages__  README
```



