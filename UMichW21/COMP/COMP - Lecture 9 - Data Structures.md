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