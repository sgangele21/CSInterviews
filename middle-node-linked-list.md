## Middle Node of Linked list

> Given a non-empty, singly linked list with head node head, return a middle node of linked list.

If there are two middle nodes, return the second middle node.


```
Example 1:

Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
```
```
Example 2:

Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.
```


```java
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
        llist.head = new Node(1);
        Node second = new Node(2);
        Node third = new Node(3);
        Node four = new Node(4);
        Node five = new Node(5);
        Node six = new Node(6);

        llist.head.next = second;
        second.next = third;
        third.next = four;
        four.next = five;
        // five.next = six;

        //System.out.println(llist.middleNode(llist.head).data);
        System.out.println(llist.middleNodeFastPointer(llist.head).data);
        // llist.printlist();

      //   1  2  3  4  5

    }

    public void printlist() {
        Node n = head;
        while (n != null) {
            System.out.print(n.data + " ");
            n = n.next;
        }
    }


  public Node middleNode(Node head) {
        if (head == null) {
            return head;
        }

        int count = 1;
        Node node = head;

        while (node != null) {
            node = node.next;
            count++;
        }

        count = count / 2;

        node = head;

        while (count > 0) {
            node = node.next;
            count--;
        }

        return node;
    }

    //   1 -> 2 ->  3 -> 4 -> 5 -> 6 -> _null_
    public Node middleNodeFastPointer(Node head) {


       if (head == null) {
            return head;
       }

      Node slow = head;
      Node fast = head;


      while(fast != null && fast.next != null) {

         slow = slow.next;
         fast = fast.next.next;  
      }


      return slow;

    }  
  }
```
