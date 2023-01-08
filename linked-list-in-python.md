# Linked List in Python

A linked list is a linear data structure that consists of a group of nodes, where each node stores a reference to an element and a reference to the next node in the list. Linked lists are useful for storing sequences of elements when the size of the list may change during the execution of a program, as they can be dynamically resized.

In Python, you can implement a linked list using the `Node` class and the `LinkedList` class. The `Node` class represents a single node in the linked list and has two instance variables: `data`, which stores the element, and `next`, which stores a reference to the next node in the list. The `LinkedList` class represents the linked list and has a head instance variable that points to the first node in the list.

Here is an example of how you can implement a linked list in Python:

```python
class Node:
    def __init__(self, data=None):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None
    
    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node
    
    def prepend(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node
    
    def delete_node(self, key):
        current = self.head
        if current and current.data == key:
            self.head = current.next
            current = None
            return
        prev = None
        while current and current.data != key:
            prev = current
            current = current.next
        if current is None:
            return
        prev.next = current.next
        current = None
    
    def print_list(self):
        current = self.head
        while current:
            print(current.data)
            current = current.next
```

You can use the `LinkedList` class to create a linked list and perform various operations on it, such as appending new nodes, prepending new nodes, deleting nodes, and printing the list.

For example, you can create a new linked list and append three nodes to it:

```python
llist = LinkedList()
llist.append("A")
llist.append("B")
llist.append("C")
```

You can also prepend a new node to the beginning of the list:

```python
llist.prepend("D")
```

You can delete a node from the list by its data:

```python
llist.delete_node("B")
```

You can print the list by traversing it and printing the data of each node:

```python
llist.print_list()
```

This will output:

```python
D
A
C
```

Here are some reference articles on the Linked List:

* [https://realpython.com/linked-lists-python/](https://realpython.com/linked-lists-python/)
    
* [https://www.tutorialspoint.com/python\_data\_structure/python\_linked\_lists.htm](https://www.tutorialspoint.com/python_data_structure/python_linked_lists.htm)
    
* [https://www.freecodecamp.org/news/introduction-to-linked-lists-in-python/](https://www.freecodecamp.org/news/introduction-to-linked-lists-in-python/)