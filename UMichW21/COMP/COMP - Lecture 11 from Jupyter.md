# Search and Sort Array


```python
import numpy as np
A=np.array([5,2,7,9,3,4,11,5])
```

We now define a function to search for the number 5 and return the indicies. The variable returns true or false and WHERE IT OCCURS


```python
def searcharray(A,value):
    n=np.size(A)
    exist='false'
    index=np.zeros(0)
    for i in range (0,n):
        if A[i]==value:
            exist='true'
            index=np.append(index,i)
    return exist,index
```


```python
exist, index = searcharray(A,5)
print(exist,index)
```

    true [0. 7.]
    

## Sorting an Array


```python
def sortarray(A):
    n = np.size(A)
    temp = 0
    for i in range(0, n):    
        for j in range(i+1, n):    
            if(A[i] > A[j]):    
                temp = A[i]    
                A[i] = A[j]    
                A[j] = temp    
    return A
```


```python
A = np.array([5,2,7,9,3,4,11,5])
sortA = sortarray(A)
print(sortA)
```

    [ 2  3  4  5  5  7  9 11]
    

There is a built in Numpy sorter as well as well!


```python
A = np.array([5,2,7,9,3,4,11,5])
A.sort()
print(A)
```

    [ 2  3  4  5  5  7  9 11]
    

## Search and sort in Matricies

You have to search across the columns and rows as well!

# Search, Insertion, Deletion in Trees!


```python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key
```

This is the same tree as defined in [[Lecture 9]]


```python
#Level 0
tree = Node(8)

#Level 1
tree.left = Node(3)
tree.right = Node(10)

#Level 2
tree.left.left = Node(1)
tree.left.right = Node(6)
tree.right.right = Node(14)

#Level 3
tree.left.right.left = Node(4)
tree.left.right.right = Node(7)
tree.right.right.left = Node(13)
```

This would is something that we would have to create an insert function or just have the tree already given.

### Search function


```python
# A function to search a given key in BST
def search(self,key):
     
    # Base Cases: root is null or key is present at root
    if self is None or self.val == key:
        return self
 
    # Key is greater than root's key
    if self.val < key:
        return search(self.right,key)
   
    # Key is smaller than root's key
    return search(self.left,key)

# A function to interpret whether the search function shows a value exists ('true') or does not exist ('false')
def exists(self,key):
    A=search(self,key)
    if A==None:
        A='false'
    else:
        A='true'
    return A
```


```python
A=(search(tree,1))
B=(exists(tree,1))

print(A)
print(B)
```

    <__main__.Node object at 0x00000203EFDDA6A0>
    true
    

### Insertion Function

Travel down the tree to find out if its bigger or smaller and place it in the correct place


```python
#A function to insert a key into the tree in the correct place
def insert(self, key):
    if self is None:
        return Node(key)
    else:
        if self.val == key:
            return root
        elif self.val < key:
            self.right = insert(self.right, key)
        else:
            self.left = insert(self.left, key)
    return self
```


```python
insert(tree, 5)
print(exists(tree,5))
```

    true
    

### Deletion Function


```python
# A function that loops down to find the leftmost leaf
def minValueNode(node):
    current = node
    while(current.left is not None):
        current = current.left
    return current

# that function is necessary to find the minimum value(leftmost leaf)
# to replace the node

#A function that deletes the node with a value "key"
def deleteNode(self, key):
 
    # Base Case
    if self is None:
        return self
 
    # If the key to be deleted is smaller than the self's key then it lies in  left subtree
    if key < self.val:
        self.left = deleteNode(self.left, key)
 
    # If the key to be deleted is greater than the self's key then it lies in right subtree
    elif(key > self.val):
        self.right = deleteNode(self.right, key)
 
    # If key is same as self's key, then this is the node to be deleted
    else:
        
        # Node with only one child or no child
        if self.left is None:
            temp = self.right
            self = None
            return temp
 
        elif self.right is None:
            temp = self.left
            self = None
            return temp
 
        # Node with two children:
        # Get the inorder successor (smallest in the right subtree)
        temp = minValueNode(self.right)
        # Copy the inorder successor's content to this node
        self.val = temp.val
        # Delete the inorder successor
        self.right = deleteNode(self.right, temp.val)
    return self
```

We want to delete node 6 from within this tree ![image.png](attachment:image.png)


```python
deleteNode(tree, 6)
print(exists(tree,6), exists(tree,7))
```

    false true
    

### Traversing Trees

Printing out the whole tree is a tedious process, but you can order the tree into an order and print it in a certain way.


```python
# A function to do inorder tree traversal
def printInorder(self):
    if self:
        # First recur on left child
        printInorder(self.left)
        # then print the data of node
        print(self.val),
        # now recur on right child
        printInorder(self.right)

# A function to do postorder tree traversal
def printPostorder(self):
    if self:
        # First recur on left child
        printPostorder(self.left)
        # the recur on right child
        printPostorder(self.right)
        # now print the data of node
        print(self.val),

# A function to do preorder tree traversal
def printPreorder(self):
    if self:
        # First print the data of node
        print(self.val),
        # Then recur on left child
        printPreorder(self.left)
        # Finally recur on right child
        printPreorder(self.right)
```


```python
printInorder(tree)
```

    1
    3
    4
    6
    7
    8
    10
    13
    14
    


```python
printPreorder(tree)
```

    8
    3
    1
    6
    4
    7
    10
    14
    13
    


```python
printPostorder(tree)
```

    1
    4
    7
    6
    3
    13
    14
    10
    8
    


```python

```
