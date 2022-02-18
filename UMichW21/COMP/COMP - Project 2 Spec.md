# COMP - Project 2 Spec

### Traffic Distribution Problems
- Assumptions
	- Travelers select a route based on minimize travel time
	- Travelers know what the travel time will be on all routes

### How to model travel time
- Empirical Data + Pattern identification
- We can count cars using technology
- The BPR function
	- Regressive model of traffic time and traffic volume
	- ![[Pasted image 20220209144027.png]]

### The UE objective function
Find the v(opt) that minimize the travel time for each user
![[Pasted image 20220209144319.png]]

### Solution Process
1. Create BPR function that takes in route data 
	1. Create ![[Pasted image 20220209144406.png]]
2. Create trapezoidal integration function
3. Create z function (as a function of just $v_o$)
	1. ![[Pasted image 20220209144519.png]]
4. Run integration to find z-values and compare your result with the analytical solution
5. Minimize z and find corresponding $v_i$
6. Check that the traffic volume ($v_i$) is below 90% capacity for each route. 

## Coding tips

### Trapezoidal integration scheme
- Area of trapezoid: $A = \dfrac{h}{2}(b_1+b_2)$
- In the context of our problem $A=\dfrac{x_1-x_0}{2}(f(x_1)+f(x_0))$
```python
# Define the function you will integrate  
def f(x):  
	return np.sqrt(x) + 2

# Define the trapezoidal integration function  
def trapezoidal_int(f_x, x):  
	# <CALCULATE AREAS>  
	return #<SUM OF AREAS>  

# Create an array of evaluation points  
x_pts = np.linspace(0, 10, 6)  

# Integrate the function evaluated at those points  
integration = trapezoidal_int(f(x_pts), x_pts)
```
- Use a for loop to go through your points!
###  Numerical Integration with symbolic bounds
```python
# Specify domain array of v_0  
v_0 = np.arange(0, 1000 + dv, dv)

# Initialize your z_0(v) array  
z_0 = np.zeros(len(v_0))  

# Loop through values of v_0 and integrate to find z_0(v)  
for j in range(len(v_0)):  
	int_range_0 = np.arange(0, v_0[j] + dv, dv)  
	z_0[j] = trapezoidal_int(t_0(int_range_0), int_range_0)  

plt.plot(v_0, z_0)

```
  - Then add the other terms within the same loop (ASK ABOUT THIS PART)
	  - ![[Pasted image 20220209150459.png]]
	
	  - Get v1 and v2 as a function of Vo
### Ad hoc Minimization
  - You can use the `min()` function
```python
import numpy as np

f = [4,1,0,1,4,9]

x = [0,1,2,3,4,5]

min_f = min(f)

x_opt = x[np.where(f(x) == min_f)]

display(x_opt)
```


4.  Other Tips
	1. https://numpy.org/doc/stable/reference/generated/numpy.where.html 
	2. https://www.w3schools.com/python/ref_func_min.asp
