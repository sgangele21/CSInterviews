## Linked List Cycle Detection

> Given a linked list, determine if it has a cycle in it.

To represent a cycle in the given linked list, we use an integer pos which represents the position (0-indexed) in the linked list where tail connects to. If pos is -1, then there is no cycle in the linked list.

https://leetcode.com/problems/linked-list-cycle/

```
Example 1:

Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```
```
Example 2:

Input: head = [1,2], pos = 0
Output: true
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

```
Example 3:

Input: head = [1], pos = -1
Output: false
Explanation: There is no cycle in the linked list.
```

```java
import java.io.*;
import java.util.*;
import java.util.HashMap;



public class Solution {
    Node head;

    static class Node {
        private int data;
        private Node next;

        public Node(int data) {
            this.data = data;
            next = null;
        }
    }

    public static void main(String[] args) {

        Solution llist = new Solution();
        llist.head = new Node(3);
        Node second = new Node(2);
        Node zero = new Node(0);
        Node four = new Node(-4);

        llist.head.next = second;
        second.next = zero;
        zero.next = four;
        four.next = second;

        //System.out.println(llist.middleNode(llist.head).data);
        //System.out.println(llist.middleNodeFastPointer(llist.head).data);
        // llist.printlist();
      System.out.println(llist.hasCycle(llist.head));


      //   1  2  3  4  5

    }

    public void printlist() {
        Node n = head;
        while (n != null) {
            System.out.print(n.data + " ");
            n = n.next;
        }
    }


  public boolean hasCycle( Node head) {
    HashMap<Integer, Node> map = new HashMap<>(); // map[node.data] = node


    Node currentNode = head;
    while(currentNode != null) {
      // Check -> Do we have the answer
      Node savedNode = map.get(currentNode.data);
      if (savedNode == currentNode)  {
        return true;
      }

      // Fall back -> No answer, let's put stuff in the map
      map.put(currentNode.data, currentNode);
      currentNode = currentNode.next;
    }
    return false;
  }
}
```
