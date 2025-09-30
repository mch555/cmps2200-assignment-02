# CMPS 2200 Assignment 2

**Name:**_________________________

In this assignment we'll work on applying the methods we've learned to analyze recurrences, and also see their behavior
in practice. As with previous
assignments, some of of your answers will go in `main.py` and `test_main.py`. You
should feel free to edit this file with your answers; for handwritten
work please scan your work and submit a PDF titled `assignment-02.pdf`
and push to your github repository.


## Part 1. Asymptotic Analysis

Derive asymptotic upper bounds of work for each recurrence below.

* $W(n)=2W(n/3)+1$
.  
.  root: 1
.  1st level:1+1 = 2, this has geometric growth
.  1<=1/c *2 
.  true when c=2. This  recurrence is leaf-dominated
.  height= log3n and # of nodes at level i is 2^i
. # nodes at level log3n: 2^(log3n) ∈ O(n^(log3*2))
 
* $W(n)=5W(n/4)+n$
.  root: n
. 1st level: 5n/4, has geometric growth
. n<=1/c *5n/4. true when c=5/4
. # levels is log4n
. # nodes at level i is 5^i --> 5^(log4n) ∈ O(n^(log4 *5))
. 
.  
.  
. 

* $W(n)=7W(n/7)+n$
.  
. root: n
.  1st level: n, recurrence is balanced
.  since it is balanced, each level does the same amount of work
.  so the max cost per level is n
.  # levels = log7n
.  so the upper bound is O(nlog7 n)

* $W(n)=9W(n/3)+n^2$
.  
. root: n^2
. 1st level: 9*n^2/9= n^2
. this recurrence is balanced, so each level does the same amount of work
. therefore, max cost per level is n^2
. # levels = log3 n
.  so upper bound of work is O(n^2 * log3 n)
.  
.

* $W(n)=8W(n/2)+n^3$
.  
. root: n^3
. 1st level: 8 * n^3/8 = n^3
. recurrence is balanced (same process as before)
. upper bound of work is therefore O(n^3 log2 n)
.  
. 
.  
. 


* $W(n)=49W(n/25)+n^{3/2}\log n$
.  
.  root: n^3/2 logn
.  1st level: 49(n^3/2 /125)log n/25 = 49/125 n^3/2 logn - 49/125 n^3/2 log25<=49/125 n^3/2 
.  there geometric decay so the recurrence is root dominated
.  n^3/2logn >= c 49/125 n^3/2 log n 
.  let c = 125/49
.  O(n^3/2 log n)
.  

* $W(n)=W(n-1)+2$
.  
.  root: 2
.  1st level: 2
.  so this recurrence is balanced
.  # levels is n and the worst level is 2
.  so upper bound of work is O(n)
.  
.  

* $W(n)= W(n-1)+n^c$, with $c\geq 1$
.  
.  root: n^c
.  1st level: if c =1 ->n is balanced
.             if c=2 ->n^2 -2n+1-> balanced
.  # levels is n
.  worse level is n^c
.  upper bound of work is O(n^(c+1))
. 

* $W(n)=W(\sqrt{n})+1$
.  root: 1
.  level 1: 1
.  balanced
.  # levels: n is decreasing like n -> n^1/2 -> n^1/4...
.  therefore n^(1/2^i) at level i and stops when n=2
.  n^(1/2^c)=2
.  log n^(1/2^c)=log2
  logn=2^c
  logn=2^c, c=log logn ( total levels )
 upperbound work is O(log logn)

## Part 2. Algorithm Comparison

Suppose that for a given task you are choosing between the following three algorithms:

  * Algorithm $\mathcal{A}$ solves problems by dividing them into
      five subproblems of half the size, recursively solving each
      subproblem, and then combining the solutions in linear time.
    
  * Algorithm $\mathcal{B}$ solves problems of size $n$ by
      recursively solving two subproblems of size $n-1$ and then
      combining the solutions in constant time.
    
  * Algorithm $\mathcal{C}$ solves problems of size $n$ by dividing
      them into nine subproblems of size $n/3$, recursively solving
      each subproblem, and then combining the solutions in $O(n^2)$
      time.

    What are the asymptotic running times of each of these algorithms?
    Which algorithm would you choose?


.  Algorithm A: 
.  root= n
.  1st level = 5n/2, geometric growth
.  work is O(n^log2 5) which is approx 
.  O(n^2.32)
. 
. Algorithm B:
. root= 1
. 1st level: 2, geometric growth
. number of leaves is 2^n because height is n so work is
. O(2^n)
. 
. Algorithm C:
. root= n^2
. 1st level: n^2, balanced
. O(n^2 logn)
. 
. algorithm B is exponential and is not practical. O(n^2 logn) grows more slowly than O(n^2.32)
. therefore, I would choose Algorithm C
## Part 3: Parenthesis Matching

A common task of compilers is to ensure that parentheses are matched. That is, each open parenthesis is followed at some point by a closed parenthesis. Furthermore, a closed parenthesis can only appear if there is a corresponding open parenthesis before it. So, the following are valid:

- `( ( a ) b )`
- `a () b ( c ( d ) )`

but these are invalid:

- `( ( a )`
- `(a ) ) b (`

Below, we'll solve this problem three different ways, using iterate, scan, and divide and conquer.

**3a. iterative solution** Implement `parens_match_iterative`, a solution to this problem using the `iterate` function. **Hint**: consider using a single counter variable to keep track of whether there are more open or closed parentheses. How can you update this value while iterating from left to right through the input? What must be true of this value at each step for the parentheses to be matched? To complete this, complete the `parens_update` function and the `parens_match_iterative` function. The `parens_update` function will be called in combination with `iterate` inside `parens_match_iterative`. Test your implementation with `test_parens_match_iterative`.


.  
. 



**3b.** What are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

**enter answer here**

.  
. 



**3c. scan solution** Implement `parens_match_scan` a solution to this problem using `scan`. **Hint**: We have given you the function `paren_map` which maps `(` to `1`, `)` to `-1` and everything else to `0`. How can you pass this function to `scan` to solve the problem? You may also find the `min_f` function useful here. Implement `parens_match_scan` and test with `test_parens_match_scan`

.  
. 



**3d.** Assume that any `map`s are done in parallel, and that we use the efficient implementation of `scan` from class. What are the recurrences for the Work and Span of this solution? 

**enter answer here**

.  
.  




**3e. divide and conquer solution** Implement `parens_match_dc_helper`, a divide and conquer solution to the problem. A key observation is that we *cannot* simply solve each subproblem using the above solutions and combine the results. E.g., consider '((()))', which would be split into '(((' and ')))', neither of which is matched. Yet, the whole input is matched. Instead, we'll have to keep track of two numbers: the number of unmatched right parentheses (R), and the number of unmatched left parentheses (L). `parens_match_dc_helper` returns a tuple (R,L). So, if the input is just '(', then `parens_match_dc_helper` returns (0,1), indicating that there is 1 unmatched left parens and 0 unmatched right parens. Analogously, if the input is just ')', then the result should be (1,0). The main difficulty is deciding how to merge the returned values for the two recursive calls. E.g., if (i,j) is the result for the left half of the list, and (k,l) is the output of the right half of the list, how can we compute the proper return value (R,L) using only i,j,k,l? Try a few example inputs to guide your solution, then test with `test_parens_match_dc_helper`.



.  
. 





**3f.** Assuming any recursive calls are done in parallel, what are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

**enter answer here**

.  
. 


 
 


