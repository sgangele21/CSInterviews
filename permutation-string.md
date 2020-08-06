## Permutation String

>Given two strings, write a method to decide if one is a permutation of the other.

```
eg. "cat" , "act"
```

They both have the same letters
Same character count
Repeating elements don't really matter when comes to permutation value

String problems involving individual characters, and their relationships to others strings' characters, use HashMaps or HashSets

In an interview, when talking about the complexity of a HashMap or HashSet, mention that it's O(1) lookup and insertion time... but that's actually an average... the worst case is O(n) from hash  collisions

```swift
import Foundation

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
