## Factorial Trailing Zeroes

> Given an integer n, return the number of trailing zeroes in n!

```
Example 1:

Input: 3
Output: 0
Explanation: 3! = 6, no trailing zero.
```

```
Example 2:

Input: 5
Output: 1
Explanation: 5! = 120, one trailing zero.
```

### Plan

- Solve the factorial, seperate method
  - Recursive



- Figure out the trailing zeros, seperate method

---

```java

import java.io.*;
import java.util.*;




class Solution {
  public static void main(String[] args) {

    Solution solution = new Solution();

    System.out.println(solution.findTrailingZero());

  }
  // x = 12120
  /*

  int temp = x % 10 // = 0
  x =



  */


  // Complexity: O(n), n being the number of digits in factorial
  public int findTrailingZero(int x) {

    // 120
    int fact = this.factorial(x);

    int counter = 0;
    // fact = 1
    while(fact != 0) {

      int temp = fact % 10; // 1
      if(temp == 0) {
        counter++;
      } else {
        break;
      }

      // Dividing by ten, shaves off the digit of any number
      fact = fact / 10; // fact = 0
    }

    return counter;

  }

// 6! = 6 * 5 * 4 * 3 * 2 * 1
// 0! = 1
// 1! = 1



  // Complexity: O(n), n being the value of input
  public int factorial(int n) {

    if(n == 1 || n == 0) {
        return 1;
    }

    return factorial(n - 1) * n;
  }




}

/*

Here's a thought

https://leetcode.com/problems/factorial-trailing-zeroes/discuss/140156/Iterative-C-Solution

public int TrailingZeroes(int n) {
        var sum = 0;
        while (n != 0) {
            sum += n/5;
            n /= 5;
        }
        return sum;
}



*/


```
