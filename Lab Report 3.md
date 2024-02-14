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
I will be using the `less` command 

1. `less -E chapter-10.txt`

```
(base) surshah@Surs-MacBook-Pro technical % less -E biomed-sizes.txt

     432    3380   24112 technical/biomed/1468-6708-3-1.txt
     533    3630   29585 technical/biomed/1468-6708-3-10.txt
     296    2166   16882 technical/biomed/1468-6708-3-3.txt
     547    4301   31378 technical/biomed/1468-6708-3-4.txt
     317    2312   18114 technical/biomed/1468-6708-3-7.txt
     411    3181   24028 technical/biomed/1471-2091-2-10.txt
     615    4684   35103 technical/biomed/1471-2091-2-11.txt
     515    3287   24851 technical/biomed/1471-2091-2-12.txt
     564    3550   27970 technical/biomed/1471-2091-2-13.txt
     339    2496   18716 technical/biomed/1471-2091-2-16.txt
     826    5832   45414 technical/biomed/1471-2091-2-5.txt
     501    3167   25458 technical/biomed/1471-2091-2-7.txt
     481    3637   25298 technical/biomed/1471-2091-2-9.txt
     537    4002   29139 technical/biomed/1471-2091-3-13.txt
     932    7125   54849 technical/biomed/1471-2091-3-14.txt
     673    4858   34209 technical/biomed/1471-2091-3-15.txt
     702    5011   35953 technical/biomed/1471-2091-3-16.txt
     642    4253   29469 technical/biomed/1471-2091-3-17.txt
     708    5587   40558 technical/biomed/1471-2091-3-18.txt
     755    5001   40379 technical/biomed/1471-2091-3-22.txt
     605    4616   33815 technical/biomed/1471-2091-3-23.txt
     699    4531   34168 technical/biomed/1471-2091-3-30.txt
    1063    7146   56000 technical/biomed/1471-2091-3-31.txt
    1013    7118   52697 technical/biomed/1471-2091-3-4.txt
     430    3136   23491 technical/biomed/1471-2091-3-8.txt
     545    3908   30279 technical/biomed/1471-2091-4-1.txt
     521    3765   28719 technical/biomed/1471-2091-4-5.txt
     784    4587   36588 technical/biomed/1471-2105-1-1.txt
     611    4414   34261 technical/biomed/1471-2105-2-1.txt
    1495    8653   68152 technical/biomed/1471-2105-2-8.txt
     455    3425   25632 technical/biomed/1471-2105-2-9.txt
     393    2665   21074 technical/biomed/1471-2105-3-12.txt
    1173    6982   54441 technical/biomed/1471-2105-3-14.txt
     776    4989   37446 technical/biomed/1471-2105-3-16.txt
     920    5988   47239 technical/biomed/1471-2105-3-17.txt
    2236    9393   78562 technical/biomed/1471-2105-3-18.txt
    2359   17408  136424 technical/biomed/1471-2105-3-2.txt
     551    3748   29117 technical/biomed/1471-2105-3-22.txt
```
The output continues. However, when using the `-E` command line argument the terminal will exit once the end of the output is reached. Once I scrolled down I was presented with the output as if the command was not called.
- [link](https://phoenixnap.com/kb/less-command-in-linux)

```
(base) surshah@Surs-MacBook-Pro technical % less -E biomed   
biomed is a directory
```

Here, it is not possible to call `less -E biomed` due to `biomed` being a directory. `less -E` cannot be used on directory.
- [link](https://phoenixnap.com/kb/less-command-in-linux)

2.`less -f chapter-10.txt`
```
432    3380   24112 technical/biomed/1468-6708-3-1.txt
     533    3630   29585 technical/biomed/1468-6708-3-10.txt
     296    2166   16882 technical/biomed/1468-6708-3-3.txt
     547    4301   31378 technical/biomed/1468-6708-3-4.txt
     317    2312   18114 technical/biomed/1468-6708-3-7.txt
     411    3181   24028 technical/biomed/1471-2091-2-10.txt
     615    4684   35103 technical/biomed/1471-2091-2-11.txt
     515    3287   24851 technical/biomed/1471-2091-2-12.txt
     564    3550   27970 technical/biomed/1471-2091-2-13.txt
     339    2496   18716 technical/biomed/1471-2091-2-16.txt
     826    5832   45414 technical/biomed/1471-2091-2-5.txt
     501    3167   25458 technical/biomed/1471-2091-2-7.txt
     481    3637   25298 technical/biomed/1471-2091-2-9.txt
     537    4002   29139 technical/biomed/1471-2091-3-13.txt
     932    7125   54849 technical/biomed/1471-2091-3-14.txt
     673    4858   34209 technical/biomed/1471-2091-3-15.txt
     702    5011   35953 technical/biomed/1471-2091-3-16.txt
     642    4253   29469 technical/biomed/1471-2091-3-17.txt
     708    5587   40558 technical/biomed/1471-2091-3-18.txt
     755    5001   40379 technical/biomed/1471-2091-3-22.txt
     605    4616   33815 technical/biomed/1471-2091-3-23.txt
     699    4531   34168 technical/biomed/1471-2091-3-30.txt
    1063    7146   56000 technical/biomed/1471-2091-3-31.txt
    1013    7118   52697 technical/biomed/1471-2091-3-4.txt
     430    3136   23491 technical/biomed/1471-2091-3-8.txt
     545    3908   30279 technical/biomed/1471-2091-4-1.txt
     521    3765   28719 technical/biomed/1471-2091-4-5.txt
     784    4587   36588 technical/biomed/1471-2105-1-1.txt
     611    4414   34261 technical/biomed/1471-2105-2-1.txt
    1495    8653   68152 technical/biomed/1471-2105-2-8.txt
     455    3425   25632 technical/biomed/1471-2105-2-9.txt
     393    2665   21074 technical/biomed/1471-2105-3-12.txt
    1173    6982   54441 technical/biomed/1471-2105-3-14.txt
     776    4989   37446 technical/biomed/1471-2105-3-16.txt
     920    5988   47239 technical/biomed/1471-2105-3-17.txt
    2236    9393   78562 technical/biomed/1471-2105-3-18.txt
    2359   17408  136424 technical/biomed/1471-2105-3-2.txt
     551    3748   29117 technical/biomed/1471-2105-3-22.txt
     573    4169   30792 technical/biomed/1471-2105-3-23.txt
     217    1602   12110 technical/biomed/1471-2105-3-24.txt
     567    4138   31764 technical/biomed/1471-2105-3-26.txt
     887    4849   38482 technical/biomed/1471-2105-3-28.txt
    1209    5760   47668 technical/biomed/1471-2105-3-3.txt
     885    5841   43797 technical/biomed/1471-2105-3-30.txt
     601    4478   34563 technical/biomed/1471-2105-3-34.txt
     543    3924   29508 technical/biomed/1471-2105-3-37.txt
     880    4126   32376 technical/biomed/1471-2105-3-38.txt
     579    4499   34817 technical/biomed/1471-2105-3-4.txt
     800    4312   34496 technical/biomed/1471-2105-3-6.txt
     641    5416   37814 technical/biomed/1471-2105-4-13.txt
     523    4551   31885 technical/biomed/1471-2105-4-24.txt
     383    2564   20276 technical/biomed/1471-2105-4-25.txt
     587    3998   29786 technical/biomed/1471-2105-4-26.txt
     400    3157   23355 technical/biomed/1471-2105-4-27.txt
     589    4371   33821 technical/biomed/1471-2105-4-28.txt
     499    3683   27649 technical/biomed/1471-2105-4-31.txt
     548    3859   29793 technical/biomed/1471-2121-1-2.txt
     478    3302   26820 technical/biomed/1471-2121-2-1.txt
     889    6396   51543 technical/biomed/1471-2121-2-10.txt
     754    5454   42311 technical/biomed/1471-2121-2-11.txt
```
The output continues. Here, using the `less -f biomed-sizes.txt` prints out the contents of the file in the terminal. To exit, you must press `q`.
```

   








  

