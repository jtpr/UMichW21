# COMP - Project 2 Spec

1. Traffic Distribution Problems
	- Assumptions
		- Travelers select a route based on minimize travel time
		- Travelers know what the travel time will be on all routes

2. How to model travel time
	- Empirical Data + Pattern identification
	- We can count cars using technology
	- The BPR function
		- Regressive model of traffic time and traffic volume
		- ![[Pasted image 20220209144027.png]]

3. The UE objective function
	Find the v(opt) that minimize the travel time for each user
	![[Pasted image 20220209144319.png]]

4. Solution Process
	1. Create BPR function that takes in route data 
		1. Create ![[Pasted image 20220209144406.png]]
	2. Create trapezoidal integration function
	3. Create z function (as a function of just $v_o$)
		1. ![[Pasted image 20220209144519.png]]
	4. Run integration to find z-values and compare your result with the analytical solution
	5. Minimize z and find corresponding $v_i$
	6. Check that the traffic volume ($v_i$) is below 90% capacity for each route. 

5. Coding tips

1. Trapezoidal integration scheme
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