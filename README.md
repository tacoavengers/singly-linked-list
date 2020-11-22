# singly-linked-list

Breakdown of a singly linked list

### Basic setup

A linked list is a linear data structure.

```
   head                                 tail
data|ref  -> data|ref -> data|ref -> data|null
```

Each node is a unit containing a piece of data and a reference pointing to the next node.  The tail node has a reference pointing to null since nothing comes after it.

- A linked list is dynamic.  Its size can be modified (e.g., adding, inserting, deleting data).
- Elements are stored randomly in memory. They can be scattered about in memory since the reference will point to the next node.

##### Pros
- Dynamic data structure.
- Insertion and deletion are easy. No need to shift all the elements when inserting or deleting a value.
- They can be used for stack queue and graphs

##### Cons
- The references to the next node require extra memory
- Random access is not possible.  To access a node one must traverse through the chain of nodes.


### Create a Linked List


Think of the ```class Node``` as a card.  It's a blank waiting for information.  It'll take in a piece of data, but does not have a ref because it doesn't know yet if it's pointing to another node.  Running this code will create a node named node1 and assign it to a space in memory.
https://repl.it/@webdevdave/TrustworthyTechnicalProcedure#main.py
```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
node1 = Node(10)
print(node1)
```
The above information is fine, but it doesn't really help us.  It's not creating a linked list of nodes.  Only a single node.    

Now to create a linked list of nodes we need a Linked List class.  In doing so, now we concern ourselves with subject of the head. After all, a list must have a head.   

#### To traverse a linked list we need to see if there's a head.    

A) If there is no head, we print out a statement indicating that.    
   
B) If the head isn't empty, we need to go through the nodes. In this case, we assign self.head to a variable 'n'. We traverse through the linked list. Notice how n.data is referring to the data value in the node, and n.ref is referring to the reference to the next node.  This will continue until the end of the list is reached.    

This will print "list is empty" since there is no node head.

```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
class LinkedList:
   def __init__(self):
      self.head = None
      
      
   def print_LL(self):         
      if self.head is None:      # A
         print("list is empty")
      else:                      # B
         n = self.head
         while n is not None:
            print(n.data)
            n = n.ref
            
LL1 = LinkedList()
LL1.print_LL()
```













