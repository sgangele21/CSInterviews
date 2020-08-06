## Two Sum Array


> Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

```
Example:

Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

Test Values:
- {-2, -7, 11, 15}, for negatives


```java
import java.io.*;
import java.util.*;
import java.util.HashMap;

class Solution {
  public static void main(String[] args) {
      int[] arr = {2, 7, 11, 15};
      //System.out.println(Array.toString(arr));
      Solution s = new Solution();

     // System.out.println(Arrays.toString(s.sum(arr, 9)));

      System.out.println(Arrays.toString(s.two_sum_fast(arr, 9)));
  }

  public int[] sum(int[]arr, int target) {
    for(int i = 0; i < arr.length; i++) {
      for(int j = 1; j < arr.length; j++) {
         if(arr[i] + arr[j] == target) {
            return new int[] {i, j};        
         }
      }
    }
    return new int[] {};
  }

  public int[] two_sum_fast(int[]arr, int target) {
    // We know the target and our current value
    // O(n)
    // 2 - 9 -> We need a 7 -> map[7] = i
    // Check map[7] -> i?,   7 - 9 -> We need a map[2] = i

    HashMap<Integer, Integer> map = new HashMap<>();

    for(int i = 0; i < arr.length; i++) {
       map.put(arr[i], i);
    }

    for(int i = 0; i < arr.length; i++) {

      int result = target - arr[i];

      if(map.containsKey(result)) {
        return new int[] {i, map.get(result)};
      }

      map.put(arr[i], i);  
    }

    return new int[] {};
  }


}
```
