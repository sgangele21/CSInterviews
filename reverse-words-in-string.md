## Reverse Words in a String

Given an input string, reverse the string word by word.

For example,
Given s = "the sky is blue",
return "blue is sky the".

```swift
import Foundation




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
