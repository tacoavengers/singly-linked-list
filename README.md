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
https://repl.it/@webdevdave/Singly-Linked-List
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
https://repl.it/@webdevdave/Add-Element-To-Beginning-of-Linked-List#main.py

```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
class LinkedList:
   def __init__(self):
      self.head = None
      
      
   def print_LL(self):         
      if self.head is None:     
         print("list is empty")
      else:                      
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
4) Since this will be the new node of the linked list, the head needs to point to the new node. Therefore, new_node = self.head.


### Adding elements to the end of a linked list
https://repl.it/@webdevdave/Python-Add-Element-to-End-of-Linked-List#main.py

[step through](http://pythontutor.com/visualize.html#code=class%20Node%3A%0A%20%20%20def%20__init__%28self,%20data%29%3A%0A%20%20%20%20%20%20self.data%20%3D%20data%0A%20%20%20%20%20%20self.ref%20%3D%20None%0A%20%20%20%20%20%20%0Aclass%20LinkedList%3A%0A%20%20%20def%20__init__%28self%29%3A%0A%20%20%20%20%20%20self.head%20%3D%20None%0A%20%20%20%20%20%20%0A%20%20%20%20%20%20%0A%20%20%20def%20print_LL%28self%29%3A%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20if%20self.head%20is%20None%3A%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20print%28%22list%20is%20empty%22%29%0A%20%20%20%20%20%20else%3A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20n%20%3D%20self.head%0A%20%20%20%20%20%20%20%20%20while%20n%20is%20not%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20print%28n.data%29%0A%20%20%20%20%20%20%20%20%20%20%20%20n%20%3D%20n.ref%0A%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20def%20add_begin%28self,data%29%3A%0A%20%20%20%20%20%20new_node%20%3D%20Node%28data%29%0A%20%20%20%20%20%20new_node.ref%20%3D%20self.head%0A%20%20%20%20%20%20self.head%20%3D%20new_node%0A%20%20%20%20%20%20%0A%20%20%20%20%20%20%0A%20%20%20def%20add_end%28self,%20data%29%3A%0A%20%20%20%20%20%20new_node%20%3D%20Node%28data%29%0A%20%20%20%20%20%20if%20self.head%20is%20None%3A%0A%20%20%20%20%20%20%20%20%20self.head%20%3D%20new_node%0A%20%20%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20%20n%20%3D%20self.head%0A%20%20%20%20%20%20%20%20%20while%20n.ref%20is%20not%20None%3A%0A%20%20%20%20%20%20%20%20%20%20%20%20n%20%3D%20n.ref%0A%20%20%20%20%20%20%20%20%20n.ref%20%3D%20new_node%0A%20%20%20%20%20%20%20%20%20%0ALL1%20%3D%20LinkedList%28%29%0ALL1.add_begin%2810%29%0ALL1.add_end%2850%29%0ALL1.add_begin%2820%29%0ALL1.print_LL%28%29&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false)
```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
class LinkedList:
   def __init__(self):
      self.head = None
      
      
   def print_LL(self):         
      if self.head is None:      
         print("list is empty")
      else:                      
         n = self.head
         while n is not None:
            print(n.data)
            n = n.ref
            
   def add_begin(self,data):
      new_node = Node(data)
      new_node.ref = self.head
      self.head = new_node
      
      
   def add_end(self, data):
      new_node = Node(data)
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


### Insert a new node inbetween two existing nodes

** First, we must decide if we're going to insert before an existing node or after an existing node.  There is a difference.

In this example, the capital letters refer to the references of the following nodes.  10 is refering to the reference A in the node valued 20 and so forth.

```
 head      A       B       C tail
10| A  -> 20|B -> 30|C -> 40|null
```

#### After a node

```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
class LinkedList:
   def __init__(self):
      self.head = None
      
      
   def print_LL(self):         
      if self.head is None:     
         print("list is empty")
      else:                     
         n = self.head
         while n is not None:
            print(n.data)
            n = n.ref
            
   def add_begin(self,data):
      new_node = Node(data)
      new_node.ref = self.head
      self.head = new_node
      
      
   def add_end(self, data):
      new_node = Node(data)
      if self.head is None:
         self.head = new_node
      else:
         n = self.head
         while n.ref is not None:
            n = n.ref
         n.ref = new_node
         
   def after_node(self, data, x):
      n = self.head
      while n is not None:
         if x == n.data:
            break
         n = n.ref
      if n is None:
         print("node is not present")
      else:
         new_node = Node(data)
         new_node.ref = n.ref
         n.ref = new_node
   
         
LL1 = LinkedList()
LL1.add_begin(10)
LL1.add_end(50)
LL1.add_end(75)
LL1.add_begin(20)
LL1.after_node(22, 50)
LL1.print_LL()

```
** data is the node value we're searching for, and x is the value we want to insert

1) We assign n to self.head
2) The loop checks while n is not None.  So if n.data is the value of x we plugged in, then we break. We found it.
3) Otherwise, we increment to the next reference via n = n.ref.  We go through the while loop again, etc.
4) If n is none, we print out that it is not present in the list.
5) Otherwise, we found the x and create a new code card and place it in the proper location in the list
5) Remember that new nodes are not pointing to anything.
6) We have to get the reference from the node we searched for and put it in the new_node reference.
Suppose this is the before picture
```
 head      A        B tail
10| A  -> 20|B ->  40|null
```
and this is the after picture
```
 head      A       B       C tail
10| A  -> 20|B -> 30|C -> 40|null
```
We inserted 30 after 20.  We need to get the reference from 20.  20 used to point to 40, now it's pointing 30. 


#### Before a node

** We must consider the possibility that a new node could be inserted before the head node.

```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
class LinkedList:
   def __init__(self):
      self.head = None
      
      
   def print_LL(self):         
      if self.head is None:     
         print("list is empty")
      else:                    
         n = self.head
         while n is not None:
            print(n.data)
            n = n.ref
            
   def add_begin(self,data):
      new_node = Node(data)
      new_node.ref = self.head
      self.head = new_node
      
      
   def add_end(self, data):
      new_node = Node(data)
      if self.head is None:
         self.head = new_node
      else:
         n = self.head
         while n.ref is not None:
            n = n.ref
         n.ref = new_node
         
   def after_node(self, data, x):
      n = self.head
      while n is not None:
         if x == n.data:
            break
         n = n.ref
      if n is None:
         print("node is not present")
      else:
         new_node = Node(data)
         new_node.ref = n.ref
         n.ref = new_node
         
   def add_before(self, data, x):
      if self.head is None:            # 1
         print("Linked list is empty")
      if self.head.data == x:          # 2
         new_node = Node(data)
         new_node.ref = self.head
         self.head = new_node
         return
      n = self.head
      while n.ref is not None:
         if n.ref.data == x:
            break                      # the purpose is just to find the ref for the data that matches x
         n = n.ref                     # otherwise continue through the loop
      if n.ref is None:
         print("could not find node")
      else:
         new_node = Node(data)
         new_node.ref = n.ref
         n.ref = new_node
      
         
LL1 = LinkedList()
LL1.add_begin(10)
LL1.add_before(20, 10)
LL1.print_LL()

```
1) If there is no head, print out that there is no head.
2) If data matches x at the head node, then we create a new node, replace the head, and move the previous head node down the chain.

#### Delete a node

```
class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
      
class LinkedList:
   def __init__(self):
      self.head = None
      
      
   def print_LL(self):         
      if self.head is None:     
         print("list is empty")
      else:                    
         n = self.head
         while n is not None:
            print(n.data)
            n = n.ref
            
   def add_begin(self,data):
      new_node = Node(data)
      new_node.ref = self.head
      self.head = new_node
      
      
   def add_end(self, data):
      new_node = Node(data)
      if self.head is None:
         self.head = new_node
      else:
         n = self.head
         while n.ref is not None:
            n = n.ref
         n.ref = new_node
         
   def after_node(self, data, x):
      n = self.head
      while n is not None:
         if x == n.data:
            break
         n = n.ref
      if n is None:
         print("node is not present")
      else:
         new_node = Node(data)
         new_node.ref = n.ref
         n.ref = new_node
         
   def add_before(self, data, x):
      if self.head is None:            # 1
         print("Linked list is empty")
      if self.head.data == x:          # 2
         new_node = Node(data)
         new_node.ref = self.head
         self.head = new_node
         return
      n = self.head
      while n.ref is not None:
         if n.ref.data == x:
            break                      # the purpose is just to find the ref for the data that matches x
         n = n.ref                     # otherwise continue through the loop
      if n.ref is None:
         print("could not find node")
      else:
         new_node = Node(data)
         new_node.ref = n.ref
         n.ref = new_node
         
         
         
   def delete_begin(self):
      if self.head is None:
         print("There are no nodes to delete")
      else:
         self.head = self.head.ref
      
   def delte_end(self):
      if self.head is None:
         print("The list is empty.  There's nothing to delete")
      else:
         n = self.head.ref
         while n.ref.ref is not None:
            n = n.ref
         n.ref = None
         
   def delete_by_value(self, x):
      if self.head is None:
         print("List is empty. Nothing to delete")
         return
      if x == self.head.data:
         self.head = self.head.ref
         return
      n = self.head
      while n.ref is not None:
         if x == n.ref.data:
            break
         n = n.ref
      if n.ref is None:
         print("Node is not here")
      else:
         n.ref = n.ref.ref
      
         
LL1 = LinkedList()
LL1.add_begin(10)
LL1.add_begin(20)
LL1.add_begin(30)
LL1.delete_by_value(10)
LL1.print_LL()

```
