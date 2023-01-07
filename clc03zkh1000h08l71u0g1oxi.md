# Tree in Python

A tree is a widely used abstract data type that consists of nodes arranged in a hierarchical structure. It is a non-linear data structure, which means that data is not stored in a sequential manner like it is in an array or linked list. Instead, data is organized into a tree-like structure, with a root node at the top and child nodes branching off from it.

In Python, you can implement a tree using a variety of data structures, such as a list, dictionary, or a custom class. One way to implement a tree in Python is to create a class called TreeNode, which has three attributes: a value, a left child, and a right child. The left child and right child are also instances of the TreeNode class, which allows us to create a hierarchical structure.

Here are some examples of working with trees in Python:

First, let's define the TreeNode class as follows:

```python
class TreeNode:
    def __init__(self, value, left=None, right=None):
        self.value = value
        self.left = left
        self.right = right
```

Now, let's create a tree by instantiating the TreeNode class and setting the left and right children of each node:

```python
root = TreeNode(1)
root.left = TreeNode(2)
root.right = TreeNode(3)
root.left.left = TreeNode(4)
root.left.right = TreeNode(5)
```

This creates a tree with the following structure:

```python
    1
   / \
  2   3
 / \
4   5
```

Now, let's say we want to perform a depth-first search on this tree. We can do this by using a stack to store the nodes that need to be visited. Here's an example of a depth-first search function that prints the values of the nodes in the tree:

```python
def depth_first_search(root):
    stack = [root]
    while stack:
        node = stack.pop()
        print(node.value)
        if node.right:
            stack.append(node.right)
        if node.left:
            stack.append(node.left)

depth_first_search(root)
```

This will print the values of the nodes in the following order: 1, 2, 4, 5, 3.

Now, let's say we want to insert a new node into the tree. To do this, we can find the appropriate location for the new node based on its value and then set it as the left or right child of the appropriate parent node. For example, let's say we want to insert a node with the value 6 as the left child of the node with the value 3:

```python
new_node = TreeNode(6)
root.right.left = new_node
```

This will modify the tree to have the following structure:

```python
    1
   / \
  2   3
 / \   \
4   5   6
```

Finally, let's say we want to delete a node from the tree. To do this, we can simply remove its references from its parent node and set them to None. For example, let's delete the node with the value 3 from the tree:

```python
root.right = None
```

This will modify the tree to have the following structure:

```python
    1
   / 
  2   
 / \
4   5
```

I hope these examples give you a better understanding of how to work with trees in Python.

***Reference:***

*   [*https://docs.python.org/3/library/stdtypes.html#trees*](https://docs.python.org/3/library/stdtypes.html#trees)
    
*   [*https://www.youtube.com/playlist?list=PLBOh8f9FoHHgPEbiK-FSNzfXUJhXbGkqG*](https://www.youtube.com/playlist?list=PLBOh8f9FoHHgPEbiK-FSNzfXUJhXbGkqG)
    
*   [https://en.wikipedia.org/wiki/Depth-first\_search](https://en.wikipedia.org/wiki/Depth-first_search)
    
*   *"Data Structures and Algorithms in Python" by Goodrich, Tamassia, and Goldwasser*