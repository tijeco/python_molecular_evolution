# Module 1, Lesson 4: Simulation of Markov processes

<!-- ## Simulation of the Poisson process


Equation 12.26

### Simulate the Poisson process of rate λ until time $t_{0}$

Step 1. Initialize t=0, N=0
Step 2. Generate a random number u, and set s <- 1/λ log(u)
Step 3. Set t <- t + s. If t > t0, stop
Step 4. Set N <- N +1, sN <- t
Step 5. Go to Step 2.



## Simulation of discrete-time Markov chains -->

Equation 12.33
Equation 12.34



### Discrete-time simulation of nucleotide substitution under the K80 model
The evolution of a nucleotide sequence is described by a discrete-time Markov chain with transition probabilities between T,C,A,G given in Equation 12.37

$$ P = \begin{bmatrix} 1-(\alpha + 2\beta) & \alpha & \beta & beta\\ \alpha &  1-(\alpha + 2\beta) & \beta & beta\\ \beta & \beta & 1-(\alpha + 2\beta) & \alpha\\ \beta & \beta & \alpha & 1-(\alpha + 2\beta) \end{bmatrix}$$

write fucntion that populates probability matrix given alpha and beta for a given model
```python
import pandas

alpha = 1e-8
beta = 1e-9






def k80matrix(alpha,beta):
  nucleotide_matrix = {"T":[],"A":[],"C":[],"G":[]}
  nucleotide_molecule = {"CT":"pyramidine","AG":"purine"}
  nucleotide_columns = ["T","A","C","G"]
  for nucleotide in nucleotide_matrix:
    for nucleotide_row in nucleotide_columns:
      if nucleotide == nucleotide_row:
        nucleotide_matrix[nucleotide].append(1 -(alpha + 2*beta))
      elif sorted(nucleotide + nucleotide_row) in nucleotide_molecule:
        nucleotide_matrix[nucleotide].append(alpha)
      else:
        nucleotide_matrix[nucleotide].append(beta)
  return pd.DataFrame.from_dict(nucleotide_matrix, orient='index', columns = nucleotide_columns)
```

Given a sequence ( or randomly generated), 'evolve' every site for time $t$. The columns in ```k80matrix()``` allow us to do this using a similiar approach to sampling nucleotides from 1.2.

```python

nucleotide_probabilities = k80matrix(alpha,beta)[nucleotide]
cdf = np.zeros(4)
for i in range(len(nucleotide_probabilities)):
  cdf[i] = nucleotide_probabilities[i] + cdf[i -1]
# [0.1,0.3,0.6,1.0]

u = random.random()
for i in range(len(cdf)):
  if u < cdf[i]:
    nucleotide = nucleotides[i]
  else:
    continue

```

The distance between two sequences separated by time $t$ is
$$ d = (\alpha +2\beta)t$$

The transition/transversion ratio is
$$ \kappa = \frac{\alpha}{\beta}$$

There are thus three distinct substitution probabilities that will be further discussed in module 2, namely $p_0(t)$, $p_1(t)$, and $p_2(t)$.

Simulating the Markov chain in $t$ steps can thus be accomplished in one step with the following equations.

$$ p_0(t) = \frac{1}{4} + \frac{1}{4}e^{\frac{-4d}{\kappa + 2}} + \frac{1}{2}e^{\frac{-2d(\kappa +1)}{\kappa + 2}}$$

$$ p_1(t) = \frac{1}{4} + \frac{1}{4}e^{\frac{-4d}{\kappa + 2}} - \frac{1}{2}e^{\frac{-2d(\kappa +1)}{\kappa + 2}}$$

$$ p_2(t) = \frac{1}{4} - \frac{1}{4}e^{\frac{-4d}{\kappa + 2}} $$

<!--
Equation 12.37
Equation 12.38
Equation 12.39

Generate random nucleotide sequence.
Evolve every site over 10 MY



## Simulation of continuous-time Markov chains


Equation 12.40
Equation 12.41

### Simulating a Markov chain over time t_{0} by using the exponential waiting times

Step 1. Set t= 0. i = X(0)
Step 2. u ~(0,1), s <- - (1/qi)log(u)
Step 3. Set t <- t + s. If t > t0, stop
Step 4. Sample new state j from discrete distribution specified by ith row of equation 112.41
Step 5. Go to step 2. -->
