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
   
B) If the head isn't empty, we need to go through the nodes. In this case, we assign self.head to a variable 'n'. We traverse through the linked list. Notice how ```n.data``` is referring to the data value in the node, and ```n.ref``` is referring to the reference to the next node.  This will continue until the end of the list is reached.    

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

### Adding elements to the beginning of a linked list

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
            
   def add_begin(self,data):
      new_node = Node(data)
      new_node.ref = self.head
      self.head = new_node
      
LL1 = LinkedList()
LL1.add_begin(10)
LL1.print_LL()
```
1) We grab a blank node class card and insert some data.
2) We assign it the variable new_node
3) The new node must have a reference to the head. That is why we have new_node.ref = self.head.
4) Since this will be the new node of the linked list, the head neds to point to the new node. Therefore, new_node = self.head.


### Adding elements to the end of a linked list

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
            
   def add_begin(self,data):
      new_node = Node(data)
      new_node.ref = self.head
      self.head = new_node
      
      
   def add_end(self, data):
      new_node = Node(data):
      if self.head is None:
         self.head = new_node
      else:
         n = self.head
         while n.ref is not None:
            n = n.ref
         n.ref = new_node
         
LL1 = LinkedList()
LL1.add_begin(10)
LL1.add_end(50)
LL1.add_begin(20)
LL1.print_LL()
```
1) We grab a blank node class card and insert some data.
2) We check to make sure there's a head.  If there isn't, we make this addition the new head.  If not, we move forward.
3) Next, we have a while loop searching until it gets to the last node.
4) Then we change the reference of the last node to the new_node.






