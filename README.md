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
- Random access is not possible.  To access a node one must traverse through the chaine of nodes.


### Create a Linked List


Think of the Class Node as a card.  It's a blank waiting for information.  It'll take in a piece of data, but does not have a ref because it doesn't know yet if it's pointing to another node.
```
Class Node:
   def __init__(self, data):
      self.data = data
      self.ref = None
   
```

```


```














