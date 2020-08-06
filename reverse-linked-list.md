## Reverse a Linked List

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
