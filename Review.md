# Review
#algorithms

## Given Two Sorted Arrays, Find Median

So for checking if statements, doing the two finger algorithm is a good way of checking stuff

My mistake was I did 
* Are both valid           -> 1
* Is p1 valid && p2 isn’t -> 2
* is p2 valid && p1 isn’t -> 3
* Are none valid           -> 4

Well, how should we arrange this so that we write the least amount of code?

We know that 4 case will never hit, so never assume this will happen

Well…. if 2 isn’t true that means that 
* p1 isn’t valid && p2 is valid 
**OR**
*  hat p1 is valid and & p2 is valid

And if you do that check again for 3, then you figure out that that either 
* p2 isn’t valid and p1 is valid
* **OR** 
* p2 is valid and so is p1

So, at the end of the day….. you trickle that logic down to -> p1 & p2 is valid….. so that’s why the order should always be the following
That’s how you reduce the most amount of code


2,3,1
or 3,2,1 

## Majority Element
If your ever inserting and searching for an element in a hash map, you’re doing something wrong
![](Review/IMG_0355.HEIC)

This code also works really well, in O(log(n) time
```java

class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        return nums[nums.length/2];
    }
}

```

Look this up: ::*Boyer-Moore Voting Algorithm*::


## Smallest Missing Positive Integer 

> Given an unsorted integer array, find the smallest missing positive integer.  


```java

// Given an unsorted integer array, find the smallest missing positive integer.

// Example 1:

// Input: [1,2,0]
// Output: 3

// Example 2:

// Input: [3,4,-1,1]
// Output: 2

// Example 3:

// Input: [7,8,9,11,12]
// Output: 1
// Note:

// Your algorithm should run in O(n) time and uses constant extra space.

// Example 4
// Input: [10,11,12,13]
// Output: 1


// Example 5
// Input: [1,3,5,7,8]
// Output: 2


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



```swift




public class Node {
  
  var data: Int?
  var next: Node?
  
  public init(_ data: Int?) {
    self.data = data  
  }
  
}


// Create nodes
let nodeOne   = Node(1)
let nodeTwo   = Node(2)
let nodeThree = Node(3)
let nodeFour  = Node(4)

// Link nodes
nodeOne.next   = nodeTwo
nodeTwo.next   = nodeThree
nodeThree.next = nodeFour


func printLinkedList(_ rootNode: Node) {
  
  var currentNode: Node? = rootNode
  while(currentNode != nil) {
   
    print(currentNode!.data)
    
    // Iterate to the next node
    currentNode = currentNode!.next
    
  }
  
}


// 1 -> |2| -> 3 -> 4 -> nil
// Return 4 -> 3 -> 2 -> 1 -> nil
func reverseLinkedList(_ rootNode: Node) -> Node {
  
  
  var currentNode:  Node? = rootNode
  var previousNode: Node? = nil 
  var nextNode:     Node? = currentNode
  
  while(currentNode != nil) {
    // Keeping moving through the list
        
    // Save temp 
    nextNode = currentNode!.next // 2
    
    // Make reverse relationship
    currentNode!.next = previousNode //nil
    
    
    // Setup for next iteration
    previousNode = currentNode 
    currentNode  = nextNode    
    
  }
  
  return previousNode!
  
}


let reversedListRoot = reverseLinkedList(nodeOne)
printLinkedList(reversedListRoot)


```



```swift

// Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

// For example:
// Given binary tree [3,9,20,null,null,15,7],
//     3
//    / \
//   9  20
//     /  \
//    15   7
// return its level order traversal as:
// [
//   [3],
//   [9,20],
//   [15,7]
// ]


public struct Queue<T> {
  fileprivate var array = [T]()

  public var count: Int {
    return array.count
  }

  public var isEmpty: Bool {
    return array.isEmpty
  }

  public mutating func enqueue(_ element: T) {
    array.append(element)
  }

  public mutating func dequeue() -> T? {
    if isEmpty {
      return nil
    } else {
      return array.removeFirst()
    }
  }

  public var front: T? {
    return array.first
  }
}


public class Node {
  
  var data: Int
  var left: Node?
  var right: Node?
  
  public init(_ data: Int) {
    
    self.data = data
    
  }
  
}


// Create Tree Nodes
let nodeThree   = Node(3)
let nodeNine    = Node(9)
let nodeTwenty  = Node(20)
let nodeFifteen = Node(15)
let nodeSeven   = Node(7)

// Link Tree Nodes
nodeThree.left   = nodeNine
nodeThree.right  = nodeTwenty
nodeTwenty.right = nodeSeven
nodeTwenty.left  = nodeFifteen

//     3
//    / \
//   9  20
//     /  \
//    15   7
// Non-recursive


//         3
//        / \
//       9  20
//      /  /  \
//     10  15   7
//    / \      
//   5   6
func levelOrderTraversal(_ rootNode: Node?) {
  
  var queue = Queue<Node>()
  
  var tempNode: Node? = rootNode // 3
  
  while(tempNode != nil) {
    
    print(tempNode!.data)
    
    //          9
    if tempNode!.left != nil {
          queue.enqueue(tempNode!.left!)

    }
    //          20
    if tempNode!.right != nil {
          queue.enqueue(tempNode!.right!)
    }
    
    tempNode = queue.dequeue()
  } 
  
}


levelOrderTraversal(nodeThree)

```
 	
## 19. Remove Nth Node From End of List

**Keys**
* The idea of removing a node, given a pointer to a node is valid….. for everything **but the last node bro….** 
* If you want to delete ANY node in a linked list… you gotta get behind that node man and delete it

Besides that…. it’s pretty simple.


## Setting the first bit of a number


```c
#include <stdio.h>
#include <stdlib.h>

int main() {
	int num = 21;
	printf("\n%d\n",num & (~1)); // 1

}
```



## 283. Move Zeros in Array 


```c


import java.io.*;
import java.util.*;

// NOTE: Test example where entire array is 0

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


/* 
Your previous C content is preserved below:


 */

```

**Need to optimize it**
[Move Zeroes - LeetCode](https://leetcode.com/problems/move-zeroes/solution/)


## 151. Reverse Words in a String

```swift

import Foundation

// Given an input string, reverse the string word by word.

// For example,
// Given s = "the sky is blue",
// return "blue is sky the".


// let str = "the sky is blue"

// let words = str.split(separator: " ") // ["the", "sky", "is", "blue"]


// var reverseStr = ""

// var reversedWords = words.reversed()

// for word in reversedWords { // ["blue", "is", "sky", "the"]
 
//   reverseStr += word
//   if reversedWords.last! != word {
//     reverseStr += " "
//   }
// }


// print(reverseStr)


let str = "the sky is blue" 

var tempStr = ""

var stack: [String] = []

for char in str {
  // Clear string when I reach space
  if char == " " {
    // tempStr is a full word
    stack.append(tempStr)
  
    // Clear tempStr, for new word
    tempStr = ""
    
  } else {
     tempStr += "\(char)" 
  }
  
}

stack.append(tempStr)

var reversedStr = ""

// Stack
while(!stack.isEmpty) {
  
  reversedStr += stack.removeLast()
  reversedStr += " "
  
}

print(reversedStr)

```

[Reverse Words in a String - LeetCode](https://leetcode.com/problems/reverse-words-in-a-string/description/)

