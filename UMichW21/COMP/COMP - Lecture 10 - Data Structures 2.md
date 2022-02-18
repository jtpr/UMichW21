# COMP - Lecture 10
- Data structures 2

## Array
- Homogeneous list of data (number, integers and character string)
- Arrays start at 0
	- ![[Pasted image 20220210120619.png]]
## Search and Sort Arrays
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

# Binary Search Tree
- Data is organized with a hierarchy
- ![[Pasted image 20220210121806.png]]
- If the child is greater than the parent, it sorts it to the right. 
### Search Operation:
![[Pasted image 20220210121911.png]]
```python
class Node:
    def __init__(self, key):
        self.left = None
        self.right = None
        self.val = key
```
I then define the same tree as in [[COMP - Lecture 9 - Data Structures]]
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


## Node deletion
- The code is somewhat complex
- If it is a leaf node:
	- ![[Pasted image 20220210123610.png]]
	- You can just delete it
- If the node has one child
	- Copy the child to the node and delete the child
	- ![[Pasted image 20220210123641.png]]
- If the node deleted has two children
	- ![[Pasted image 20220210123739.png]]
	- Copy the child with the lesser value to the node and delete the child


## Traversal Trees

Printing out the whole tree is a tedious process, but you can order the tree into an order and print it in a certain way:
### In-order traversal
- Start at the left and move to the right (generally in ascending order!)
- ![[Pasted image 20220210124743.png]]
- Psedocode:
	- ![[Pasted image 20220210124908.png]]

### Pre-Order Traversal
- Root node is visited first, then the left subtree and the right subtree
- ![[Pasted image 20220210124955.png]]
- ![[Pasted image 20220210125018.png]]

### Post - Order Traversal
- Visit the left subtre, then the right subtree than the node
![[Pasted image 20220210125107.png]]

>>> CODE



# INTEGRATE THESE TWO DOCUMENTS TOGETHER
- [[COMP - Lecture 11 (Jupyter)  1]]