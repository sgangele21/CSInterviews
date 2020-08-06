## Level Order Traversal
> Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

```
For example:
Given binary tree [3,9,20,null,null,15,7],
    3
   / \
  9  20
    /  \
   15   7
return its level order traversal as:
[
  [3],
  [9,20],
  [15,7]
]
```

```java
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
