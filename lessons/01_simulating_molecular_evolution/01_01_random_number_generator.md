# Module 1, Lesson 1: Random number generator

# Topics covered in slides
  * Stochastic simulation
  * Uniform distribution
  * Hardware random number generators
  * Pseudo-random numbers
  * Random number seed

[slides](ref)



<!-- ![alt](https://www.astroml.org/_images/fig_uniform_distribution_1.png) -->

## multiplication-congruential method


$$ A_{i} = cA_{i-1} mod M $$

In this equation, $A_{i}$, $c$, and $M$ are all positive integers. The multiplier is $c$, the remainder when a is divided by M is a mod M. In python this would be ```a%M```
$$ ui = \frac{A_{i}}{M} $$



```python
#
M = 10000
c = 13
A0 = 123
A1 = ((c*A0)%M)
u1 = A1/M
```

## Worked exercise
1. Make a function to construct array A of length N given c = 13,A0 = 123, M = 10000


```python
  def func A_N(c,A0,M,N):
    A = [((c*A0))] # such that A[0] = A0
    for n in range(1,N):
      A.append(((c*A[n-1])%M))
    return A

```

2. Make array u, for all in A, given M = 10000

```python
  def func u_N(A,M):
    u = []
    # A = [((c*A0)%M)] # such that A[0] = A0
    for i in range(len(A)):
      u[i] = A/M
      A.append(((c*A[n-1])%M))
    return A
```

## On your own

Make a function that combines the previous two functions called mult_congruiential(c,A0,N,M)



## random number seed and running simulations on computer clusters

```python
import random
random.random()
# play around with seed
```

Python rand()

## Problem

similiar to 12.1
