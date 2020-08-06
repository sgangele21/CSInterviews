## Move Zeros in Array


Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Example:

```
Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
Note:
```

You must do this in-place without making a copy of the array.
Minimize the total number of operations.

```java
import java.io.*;
import java.util.*;

class Solution {
  public static void main(String[] args) {



    int[] num = {0,1,0,3,12};

    Solution solution = new Solution();

    int[] newNum = solution.shiftZeros(num);

    //System.out.println(newNum);
    for(int i = 0; i < newNum.length; i++) {
      System.out.println(newNum[i]);  
    }
  }

  public void swap(int[] num, int i, int j) {
    int temp = num[i];
    num[i] = num[j];
    num[j] = temp;
  }

    //  int[] num = [0,1,0,3,13]


  public int[] shiftZeros(int[] num) {
    int zCount = 0;


    for(int i = 0; i < num.length; i++) {
     if(num[i] == 0) {
        for(int j = i; j < (num.length - zCount - 1); j++) {
         swap(num, j, j + 1);
        }
         zCount =+ 1;
      }
    }
    return num;
  }

}

```

**Need to optimize it**
[Move Zeroes - LeetCode](https://leetcode.com/problems/move-zeroes/solution/)
