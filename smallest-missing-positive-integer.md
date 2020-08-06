## Smallest Missing Positive Integer

> Given an unsorted integer array, find the smallest missing positive integer.  

```
Example 1:

Input: [1,2,0]
Output: 3
```

```
Example 2:

Input: [3,4,-1,1]
Output: 2
```

```
Example 3:

Input: [7,8,9,11,12]
Output: 1
```

```
Example 4
Input: [10,11,12,13]
Output: 1
```

```
Example 5
Input: [1,3,5,7,8]
Output: 2
```

**Note:**

Your algorithm should run in O(n) time and uses constant extra space.

```java
import java.io.*;
import java.util.*;

class Solution {
  public static void main(String[] args) {

    // Write Here
    int[] nums = {2,3,1,5};

    Solution s = new Solution();

    int num = s.missingSmallestInteger(nums);
    System.out.println(num);
  }

  // Hashing Solution
  public int missingSmallestInteger(int[] num) {
      // Min heap
      HashSet<Integer> set = new HashSet<Integer>();
      int smallestNum = 1;

      // Put all the elements in the set O(n)
      for(int i = 0; i < num.length; i++) {
        set.add(num[i]);
      }

      // While the set does contain smallest Num O(n)
      while(set.contains(smallestNum)) {

         smallestNum += 1;

      }

    // O(n) + O(n) = O(2n) = O(n)

    return smallestNum;
  }  

//   // Hashing Solution
//   // num = {2,3,1,5}
//   public int missingSmallestInteger(int[] num) {
//       // Min heap
//       HashSet<Integer> set = new HashSet<Integer>();
//       int smallestNum = 1;

//     // Put all the elements in the set O(n)
//       for(int i = 0; i < num.length; i++) {
//         set.add(num[i]);
//       }

//       // While the set does contain smallest Num O(n)
//       while(set.contains(smallestNum)) {

//          smallestNum += 1;

//       }

//     // O(n) + O(n) = O(2n) = O(n)

//     return smallestNum;
//   }




  // Heap Solution
//   // num = {2,3,1,5}
//   public int missingSmallestInteger(int[] num) {
//       // Min heap
//       PriorityQueue<Integer> pQueue = new PriorityQueue<Integer>();
//       int smallestNum = 1;

//       for(int i = 0; i < num.length; i++) {
//         pQueue.add(num[i]);
//       }
//     // {1,2,3,5}
//       while(pQueue.size() != 0) {
//          if(smallestNum == pQueue.poll()){
//                smallestNum += 1;
//           }

//       }

//     return smallestNum;
//   }

}

```

So we did a problem on the following:
**Find the smallest missing positive number**
Now this is a little confusing so let’s break it down
* Number -> We know we’re dealing with Integers. No floats, Doubles etc.
* Smallest -> This means means a very very small number.... the smallest number possible from a set of numbers [-inf,, +inf]
* Positive -> This narrows our scope to [1,+inf], since 0 is neither positive nor negative
* Find Missing -> This means that we are given a set of numbers with the range of [-inf,+inf], and now we want to look at the numbers from [1, +inf] and see if what is the smallest number in [1, +inf] that we are missing?

The wording is tricky, but makes sense after examples:

*Example 1:*
Input: [1,2,0]
Output: 3

*Example 2:*
Input: [3,4,-1,1]
Output: 2

*Example 3:*
Input: [7,8,9,11,12]
Output: 1

*Example 4:*
Input: [10,11,12,13]
Output: 1

*Example 5:*
Input: [1,3,5,7,8]
Output: 2

~After the examples, everything makes sense~

So let’s get into the logic of the problem... we solve it using two ways, one with heap, the other using a hash.

~Heap~
* Create a heap, and store all elements in there
* Then poll all the elements (which will be in order), and check the smallestNum starting from 1, if  it’s equal to the current poll from the heap
    * YES: Increment smallestNum
    * NO: Return smallestNum
* This uses O(nlog(n)) time, and O(n) space

~Hash~
* Create a hash set, since we we only need to insert, and check if elements are in the set in O(1) average time
* Insert all elements into the set
* Now, have a smallestNum value being 1, and check if the smallestNum value is in the set
    * YES, it’s in the set: Then we move on to the next smallest num -> 2
    * NO, it’s not in the set: Then we return our smallestNum
* This uses O(n) time, and O(n) constant space

**Take aways**
* Never write code like `int smallestNum=1;` , because this is very unreadable… put spaces in-between
* We learned the main methods for a JavaHashMap
    * `add(E e)` -> Adds a entry into set (unique elements are only in set), O(1) average time
    * `contains(E e) -> Bool` -> Checks to see if entry is in set, O(1) average time
* And for Heaps
    * `add(E e)` ->  O(log(n)) average, best O(n)
    * `poll() -> E`  -> O(log(n))
