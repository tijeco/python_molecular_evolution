# Module 1, Lesson 1: Random number generator

## random numbers

uniform distribution = U(0,1)
draw random number u
u ~ U(0,1)

## hardware random number generators
Truly random. Too slow for computers to use
## pseudo-random number generators
Mathematical approach to generate number between 0-1. Appears random.
## multiplication-congruential method

$$ A_{i} = cA_{i-1} mod M $$
$$ ui = \frac{A_{i}}{M} $$


## random number seed and running simulations on computer clusters

Deterministic.
Sufficiently large number.
Number of seconds passed since 00:00:01 1 January 1970

Python rand()

## Problem

similiar to 12.1
