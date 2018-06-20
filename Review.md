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


## Find whether all the character in a string are unique


```java

import java.io.*;
import java.util.*;

/*
    Determine if all the characters of a string are unique!
    Example:  isUnique("Sahil")   --> True
              isUnique("Gangele") --> False
       If the string has repeating characters then the string is unique         

    run a for loop around the string
*/


class Solution {
  public static void main(String[] args) {
        
        String name = "Sahil";
        char[] arr = name.toCharArray();
    
    
        Solution s = new Solution();
        System.out.println(s.isUnique(arr));
    
  }
  
  // O(n) complexity
  public boolean isUnique(char str[]) {
    
    //Creates an empty hashset
    HashMap<Character, Character> set = new HashMap<>();
     
    // Iterating through the string
    for(int i = 0; i < str.length; i++) {
        // stores each character of the string 
       char character = str[i]; 
      if(!set.contains(character)) { 
          hash.put(character,character); 
      }
      else {
          return false;
      }
      
    }
      return true;
  }
  
}

/*
Hash Set
- O(1) look up time: .contains()
- O(1) insertion: .add()
- Never use a hash
*/


```



## Permutation String



```swift

import Foundation


// Given two strings, write a method to decide if one is a permutation of the other.
// eg. "cat" , "act"
// They both have the same letters 
// Same character count
// Repeating elements don't really matter when comes to permutation value

// String problems involving individual characters, and their relationships to others strings' characters, use HashMaps or HashSets
// In an interview, when talking about the complexity of a HashMap or HashSet, mention that it's O(1) lookup and insertion time... but that's actually an average... the worst case is O(n) from hash  collisions

// Precondition: All strings are lowercase
// Complexity: O(n^2)
func isPermutation(_ strOne: String, _ strTwo: String) -> Bool {
     if strOne.count != strTwo.count {
        return false // Not a permutation 
     }
  
    // Both strings are the same size
    for i in 0..<strOne.count {
      let charOne = strOne[strOne.index(strOne.startIndex, offsetBy: i)]
      let charTwo = strTwo[strTwo.index(strTwo.startIndex, offsetBy: i)]
      // Is the letter in strOne in strTwo | Is the letter in strTwo in strOne
      if !strTwo.contains(charOne) || !strOne.contains(charTwo)  {
         return false // We know  
      }
    }
    return true
}


func isPermutationSpeedy(_ strOne: String, _ strTwo: String) -> Bool {
     if strOne.count != strTwo.count {
        return false // Not a permutation 
     }
  
    var mapOne: [Character: Character] = [ : ]
  
    // Both strings are the same size
    // I put every single character in strOne inside of mapOne
    // O(n)
    for i in 0..<strOne.count {    
      let charOne = strOne[strOne.index(strOne.startIndex, offsetBy: i)]
      // O(1)
      mapOne[charOne] = charOne
    }
  
    // O(n)
    for i in 0..<strTwo.count {    
      let charTwo = strTwo[strTwo.index(strTwo.startIndex, offsetBy: i)]
      // If a character from strTwo is NOT inside mapOne.... it's not a permutation
      // O(1)
      if(mapOne[charTwo] == nil) {
        return false
      }
    }
    return true
}


func isPermutationSpeedySorted(_ strOne: String, _ strTwo: String) -> Bool {
    let sortedStrOne = strOne.sorted()
    let sortedStrTwo = strTwo.sorted()
    return sortedStrOne == sortedStrTwo
}


/*
ASCII Solution

'a' = 0
'b' = 1
'c' = 2
'd' = 3

('abc', 'cba')

var array = [0,0,0]
let strOne = 'abc'

strOne.charAt(0) -> 'a'
array[0] += 1

New array = [1,0,0]

strOne.charAt(0) -> 'b'
array[1] += 1

New array = [1,1,0]

.
.
.

Array = [1,1,1]

let strTwo = 'cda'

strTwo.charAt(0) -> 'c'
array['c'] -= 1..... This should be 0

Array = [1,1,0,0]


strTwo.charAt(1) -> 'd'
array[3] -= 1
[1,1,0,-1]...... Do a check, does this value turn to negative 1?

*/



let isPermute = isPermutationSpeedySorted("cat","tac")
// Test Cases: 
// (sahil,hilaas)
// (aaaaaa,aaaaas)
// (cat,tac)



print("Is Permutation: \(isPermute)")


// Permutations -> Order matters.
/* eg. Of Permutations
Formula: n! / (n - r)!
- n: Group of objects
- r: Selection of objects

{1,2,3}
{2,3,1}
{3,1,2}
{2,1,3}
{1,3,2}
{3,2,1}
r: 3
n: 3

*/


// Combinations -> Order DOESN'T matter.
/* eg. Of Combinations

Example: Lottery Pick Given 49 balls, select 6 numbers


https://en.wikipedia.org/wiki/Lottery_mathematics -> Read up on


49*48*47*46*45*44 -> _ _ _ _ _ _ How many numbers can we make from 6 unique digits  

n: 49
r: 6


{#,#,#}


Dinner table with 9 chairs, 9 people

1     2    3    4
_     _    _    _

Permutation
n: 9
r: 9

9! / (9 - 9)!

- If n & r are the same, permuation problem is just a factorial of n

*/

```


## Factorial Trailing Zeroes

```

import java.io.*;
import java.util.*;

//172. Factorial Trailing Zeroes
// Given an integer n, return the number of trailing zeroes in n!

/*
Example 1:

Input: 3
Output: 0
Explanation: 3! = 6, no trailing zero.

------------

Example 2:

Input: 5
Output: 1
Explanation: 5! = 120, one trailing zero.

*/

/*
----Plan----

- Solve the factorial, seperate method
  - Recursive



- Figure out the trailing zeros, seperate method

*/



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