# Data Structures

## Array
- Homogeneous list of data (Number, int, character string)
- ![[Pasted image 20220206173252.png]]
- Python indexes from 0
- Building blocks to other data structures
- Used for different sorting algorithms 

Python examples:
```python
import numpy as np
cars = np.array(["Toyota", "Honda", "Ford"])

# print each element using a for loop

for x in cars:
	print(x)
```
The datatype is implied by how we define the array.
```python
float1 = np.array([5.,2.,9.])
# OR
float2 = np.array([5,2,9], dtype = 'float64')

# To check the type of array present
print(float1.dtype, float2.dtype
```
We can get the size and index into the array
```python

# Size
nelements = np.size(cars)
print(nelements)

# Index into the array
print(cars[1]) # >> Honda

# WE can also print the elements of an array using a for loop
for i in range (0,nelements): # for loops is not inclusing (0, 1, 2)
	print(i, cars[i])

# We append an element to an array
cars = np.append(cars, "Ferrari")

# WE delete an element from the array
cars = np.delete(cars,1) # >> Deletes Honda from the list
```

[Continue from 15:00]

## Matrices
- A matrix is a 2D array, each element is characterized by 2 indices (i,j) starting at 0. (row, column)

```python

A = np.array([[6,9,2],[1,7,1]]) # comma between rows
print(A)

# index into different parts of the matrix:
print(A[1,1])

>> 7

# you can find the dimensions as well
rows = np.size(A,0) # 0 for rows
columns = np.size(A, 1) # column

# Print in a for loop
for i in range (0, rows):
	print([A[i,0], A[i,1], A[i,2]])

```

## Trees
![[Pasted image 20220219133850.png]]
Think of files and folders on your computer!

### Binary Search Tree
- there are only 2 children for each parent
	- ![[Pasted image 20220219134045.png]]
	- If it is a smaller number it goes to the left
	- If it is a bigger number it goes to the right
- Every node has attributes
	- **key** - value stowed in the node
	- **Left** - left pointer
	- **right** - right pointer
	- **P** - Parent

##### Example
Place the numbers in the binary search tree: 10, 14, 8, 12, 22, 9, 19, 15, 11
![[Pasted image 20220219134530.png]]

Python implementation
To implement the tree in python we first define a class with the properties of the node. 

```python

class Node:
	def __init__(self, data):
		self.left = None
		self.right = None
		self.data = data
```

Now we can define the tree directly
```python
# Level 0
root = Node(8)

# Level 1
root.left = Node(3)
root.right = Node(10)

# Level 2
root.left.left = Node(1)
root.left.right = Node(6)
root.right.right = Node(14)

# Level 3
root.left.right.left = Node(4)
root.left.right.right = Node(7)
root.right.right.left = Node (13)

```


## Networks: Edge lists
- Edge lists represent adjacent vertices
	- List the pair of outgoing arrows!
		- 1-6
		- 2-1
		- 2-5
		- 3-2
		- 3-5
- ![[Pasted image 20220219135029.png]]

## Networks: Adjacency Matrices
- Edges add a 1 and loops add a 2
- ![[Pasted image 20220219135225.png]]