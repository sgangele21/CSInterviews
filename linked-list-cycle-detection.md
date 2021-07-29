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
Slow - fast pointer implementation

```java
public class loop_detection {
    Node head;

    private class Node {
        Node next;
        int data;

        public Node(int data) {
            this.data = data;
            this.next = null;
        }
    }

    public static void main(String[] args) {
        loop_detection ll = new loop_detection();
        ll.append(20);
        ll.append(4);
        ll.append(15);
        ll.append(10);

        ll.head.next.next.next.next = ll.head;
        ll.loop();


    }

    /**
     * solution1: fast and slow pointer/  Floyd's cycle finding algorithm
     * traverse a linked list using two pointers.
     * move one pointer by one and another pointer by two
     * if these pointers meet at the same node then there is a loop.
     * if these pointers do not meet then the linked list doesn't have a loop
     * Only one traversal is needed. The time complexity is O(n)
     */
    public void loop() {
        int flag = 0;
        Node slowPointer = head;
        Node fastPointer = head;

        while (slowPointer != null && fastPointer != null && fastPointer.next != null) {
            fastPointer = fastPointer.next.next;
            slowPointer = slowPointer.next;

            if (fastPointer == slowPointer) {
                flag = 1;
                break;
            }

        }
        if (flag == 1) {
            System.out.println("loop found");
        } else {
            System.out.println("loop not found");
        }
    }

```