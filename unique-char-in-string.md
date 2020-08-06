## Find whether all the character in a string are unique

> Determine if all the characters of a string are unique!

```
Example:  isUnique("Sahil")   --> True
          isUnique("Gangele") --> False
```

```java

import java.io.*;
import java.util.*;

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
