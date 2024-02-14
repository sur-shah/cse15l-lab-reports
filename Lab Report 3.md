# Lab Report 3


## Part 1 - Bugs


### One of the bugs from the week 4 lab was in the reversed method.


**A failure inducing input for the buggy program written as a JUnit Test.**


```
@Test
  public void testReversed() {
    int[] input1 = {1,2,3,4};
    assertArrayEquals(new int[]{4,3,2,1}, ArrayExamples.reversed(input1));
  }
}
```

Here instead of returning [4,3,2,1] it will instead return [0,0,0,0]. This is because in the reverse method it is returning the input `arr` which is being cleared instead of the `newArray`. However, there is implementation issues that will be adressed later.

**An input that *doesn't* induce a failure**

```
@Test
  public void testReversed() {
    int[] input1 = {0,0,0,0};
    assertArrayEquals(new int[]{0,0,0,0}, ArrayExamples.reversed(input1));
  }
}
```

Here when inputting an array of [0,0,0,0] the `reversed` method will also return [0,0,0,0]. When using the reverse array with all zeros, the values do not change, making this test case pass.

**The sympton, as the output of running the tests**

![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/cbb42cb6-b588-4185-b9d8-3a25b17d4e3c)

![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/477d85f5-1076-4259-8600-00a4ae4f7cd5)

These are the two examples of the tests in which the first one fails and where the second one passes.

**The bug, as the before-and-after code change required to fix it**

```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  ```

  
  ```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
  ```
  
These are the two code blocks. The first one is the before which is the incorrect implementation of the reversed method. This is because it returns an array of all zeros. Instead, the fix in the second one is that it assigns the values of `newArray` to be the values of the input `arr` reversed correctly, without losing previous data.

## Part 2 - Researching Commands

I will be using the `find` command 

### -mtime [x days] (file input)

**Example 1 - file**

```
(base) surshah@Surs-MacBook-Pro technical % find ./biomed-sizes.txt -mtime -7
./biomed-sizes.txt
```

Here, this command returns the file name if it has been modified within x days. In this case, the parameter is set to seven days, and it was infact modified within seven days.

**Example 1- directory**

```
(base) surshah@Surs-MacBook-Pro technical % find ./biomed -mtime -7
./biomed
./biomed/1472-6807-2-2.txt
./biomed/1471-2350-4-3.txt
./biomed/1471-2156-2-3.txt
./biomed/1471-2156-3-11.txt
./biomed/1471-2121-3-10.txt
./biomed/1471-2172-3-4.txt
./biomed/gb-2002-4-1-r2.txt
./biomed/gb-2003-4-6-r41.txt
./biomed/1471-2466-1-1.txt
./biomed/1471-2199-2-10.txt
./biomed/1471-2202-2-9.txt
./biomed/cc991.txt
./biomed/1471-2369-3-9.txt
...
./biomed/1476-4598-1-6.txt
```

Here, since the `biomed` directory has been modified within the seven days as specified in the parameter, the command lists the files within the directory.

### -size (size)

**Example 2 - file**

```
(base) surshah@Surs-MacBook-Pro technical % find ./biomed-sizes.txt -size +1M
(base) surshah@Surs-MacBook-Pro technical %
```

Here, since the file `biomed-sizes.txt` is not larger than 1 megabyte, it was not listed. However, if it was bigger than 1 mb, the filename would be printed in terminal. The `+` means to search to see if it is `larger` than 1Mb.

**Example 2 - directory**

```
(base) surshah@Surs-MacBook-Pro technical % find ./biomed -size -1M
./biomed
./biomed/1472-6807-2-2.txt
./biomed/1471-2350-4-3.txt
./biomed/1471-2156-2-3.txt
./biomed/1471-2156-3-11.txt
./biomed/1471-2121-3-10.txt
./biomed/1471-2172-3-4.txt
./biomed/gb-2002-4-1-r2.txt
./biomed/gb-2003-4-6-r41.txt
./biomed/1471-2466-1-1.txt
./biomed/1471-2199-2-10.txt
./biomed/1471-2202-2-9.txt
./biomed/cc991.txt
./biomed/1471-2369-3-9.txt
...
./biomed/1476-4598-1-6.txt
```

Here, the directory `biomed` is smaller than 1 Mb, so all the files are listed within in the directory. If this was not the case, nothing would be printed.

### -type (file type)

**Example 3 - file**

```
surshah@Surs-MacBook-Pro technical % find ./biomed-sizes.txt -type f
./biomed-sizes.txt
```

the `-type f` command line argument checks to see if the input paramater where `./biomed-sizes.txt` is is a normal file (f). There are various aspects that can be used and would change the output. 

**Example 3 - directory**

```
surshah@Surs-MacBook-Pro technical % find ./biomed -type d
./biomed
```

the `-type d` command line argument checks to see if the input paramater (in this case the directory `biomed`) is of type directory (d). Because it is in fact a directory, the name of the directory will be printed in the terminal.

### -print

**Example 4- file**

```
(base) surshah@Surs-MacBook-Pro technical % find ./biomed-sizes.txt -print
./biomed-sizes.txt
```

Using the `-print` command on a file prints out its relative path. 

**Examples 4- directory**

```
(base) surshah@Surs-MacBook-Pro technical % find ./biomed -name "*.txt" -print
./biomed/1472-6807-2-2.txt
./biomed/1471-2350-4-3.txt
./biomed/1471-2156-2-3.txt
./biomed/1471-2156-3-11.txt
./biomed/1471-2121-3-10.txt
./biomed/1471-2172-3-4.txt
./biomed/gb-2002-4-1-r2.txt
./biomed/gb-2003-4-6-r41.txt
./biomed/1471-2466-1-1.txt
./biomed/1471-2199-2-10.txt
./biomed/1471-2202-2-9.txt
./biomed/cc991.txt
./biomed/1471-2369-3-9.txt
./biomed/bcr620.txt
./biomed/1476-069X-2-4.txt
./biomed/1472-6750-3-11.txt
./biomed/1471-2164-2-9.txt
./biomed/1471-2091-2-10.txt
./biomed/gb-2001-2-4-research0010.txt
...
./biomed/1476-4598-1-6.txt
```

Using the `-print` command on the directory prints out all of the paths of the `.txt` files within the directory.









   








  

