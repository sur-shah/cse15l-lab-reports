# Lab Report 3


## Part 1 - Bugs


### One of the bugs from the week 4 lab was in the reversed method.


**A failure inducing input for the buggy program written as a JUnit Test.**


`@Test
  public void testReversed() {
    int[] input1 = {1,2,3,4};
    assertArrayEquals(new int[]{4,3,2,1}, ArrayExamples.reversed(input1));
  }
}
`


Here instead of returning [4,3,2,1] it will instead return [0,0,0,0]. This is because in the reverse method it is returning the input `arr` which is being cleared instead of the `newArray`. However, there is implementation issues that will be adressed later.


**An input that *doesn't* induce a failure**
`@Test
  public void testReversed() {
    int[] input1 = {0,0,0,0};
    assertArrayEquals(new int[]{0,0,0,0}, ArrayExamples.reversed(input1));
  }
}
`


Here when inputting an array of [0,0,0,0] the `reversed` method will also return [0,0,0,0]. When using the reverse array with all zeros, the values do not change, making this test case pass.

**The sympton, as the output of running the tests**
![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/209fc69b-12b9-49ff-beaf-38057541d905)


![image](https://github.com/sur-shah/cse15l-lab-reports/assets/156368641/b89ad920-287e-473e-9ee1-c56b20d396ff)


These are the two examples of the tests in which the first one fails and where the second one passes.

**The bug, as the before-and-after code change required to fix it**
`static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  `

  
  `static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
  `

  
These are the two code blocks. The first one is the before which is the incorrect implementation of the reversed method. This is because it returns an array of all zeros. Instead, the fix in the second one is that it assigns the values of `newArray` to be the values of the input `arr` reversed correctly, without losing previous data.

## Part 2 - Researching Commands




  

