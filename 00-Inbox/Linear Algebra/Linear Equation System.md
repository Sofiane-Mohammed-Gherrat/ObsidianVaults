
### Sources:
1. **Intro**: https://www.youtube.com/watch?v=csgNflj69-Y
2. **Matrices**: https://www.youtube.com/watch?v=y6bVhgmy2rw

A **system of linear equations** is a set of two or more linear equations that involve the _same_ set of variables and are considered all at once. ([Wikipedia](https://en.wikipedia.org/wiki/System_of_linear_equations?utm_source=chatgpt.com "System of linear equations"))

---

### Key points:

- A _linear equation_ in variables (x_1, x_2, …, x_n) has the form  
    [  
    a_1x_1 + a_2x_2 + \cdots + a_nx_n = b  
    ]  
    where the (a_i) and (b) are constants and the variables appear only to the first power and are not multiplied together. ([Wikipedia](https://en.wikipedia.org/wiki/Linear_equation?utm_source=chatgpt.com "Linear equation"))
    
- A _system_ means we have multiple such equations with the _same_ variables. For example:  
    [ 
    \begin{cases}  
    2x + 3y = 6 \  
    4x - 2y = 8  
    \end{cases}  
    ]  
    is a system of two linear equations in the two variables (x) and (y). ([Math is Fun](https://www.mathsisfun.com/algebra/systems-linear-equations.html?utm_source=chatgpt.com "Systems of Linear Equations - Math is Fun"))
    
- The _solution_ to the system is a set of values for the variables ((x_1, x_2, …, x_n)) that simultaneously satisfy _all_ of the equations in the system. ([textbooks.math.gatech.edu](https://textbooks.math.gatech.edu/ila/systems-of-eqns.html?utm_source=chatgpt.com "Systems of Linear Equations"))
    
- Systems of linear equations can be classified as:
    
    - **Consistent**: Has at least one solution. ([personal.math.ubc.ca](https://personal.math.ubc.ca/~tbjw/ila/systems-of-linear-equations.html?utm_source=chatgpt.com "Systems of Linear Equations"))
        
    - **Inconsistent**: Has no solution. ([personal.math.ubc.ca](https://personal.math.ubc.ca/~tbjw/ila/systems-of-linear-equations.html?utm_source=chatgpt.com "Systems of Linear Equations"))
        
    - Additionally, when there _is_ a solution it might be a _unique_ solution or _infinitely many_ solutions, depending on how the equations relate. ([textbooks.math.gatech.edu](https://textbooks.math.gatech.edu/ila/systems-of-eqns.html?utm_source=chatgpt.com "Systems of Linear Equations"))
        
- They can be written in _matrix form_:  
    [  
    A,\mathbf{x} = \mathbf{b}  
    ]  
    where (A) is a matrix of coefficients, (\mathbf{x}) is the vector of variables, and (\mathbf{b}) is the constants vector. ([GeeksforGeeks](https://www.geeksforgeeks.org/system-linear-equations/?utm_source=chatgpt.com "System of Linear Equations - GeeksforGeeks"))
    

---

### Geometric intuition

- In two variables (x) and (y): each linear equation corresponds to a straight line in the plane. The solution to the system is the point(s) where the lines intersect (if they do). ([textbooks.math.gatech.edu](https://textbooks.math.gatech.edu/ila/systems-of-eqns.html?utm_source=chatgpt.com "Systems of Linear Equations"))
    
- If the lines intersect at exactly one point → one solution.
    
- If they are parallel and distinct → no solution (inconsistent).
    
- If they coincide (the same line) → infinitely many solutions (every point on that line works).
    
- Similarly in three variables each equation is a plane in 3-D; the intersection of planes (line, point, none) corresponds to the solution set. ([personal.math.ubc.ca](https://personal.math.ubc.ca/~tbjw/ila/systems-of-linear-equations.html?utm_source=chatgpt.com "Systems of Linear Equations"))
    

---

### Why is this important?

Systems of linear equations are foundational in many fields — physics, engineering, economics, computer science — because they often model multiple constraints acting on multiple unknowns. They also form the core of much of linear algebra. ([Wikipedia](https://en.wikipedia.org/wiki/System_of_linear_equations?utm_source=chatgpt.com "System of linear equations"))

---

### Summary

In short: A system of linear equations is just “several linear equations” sharing the same unknowns, and solving it means finding values of those unknowns that make _every_ equation true at the same time.