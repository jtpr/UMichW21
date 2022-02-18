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


