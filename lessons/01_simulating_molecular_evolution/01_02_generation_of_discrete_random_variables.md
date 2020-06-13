# Module 1, Lesson 2: Generation of discrete random variables

See slides for information about
* probability mass function
* Cumulative distribution function
* Discrete uniform distribution


## Inversion method for sampling from a general discrete distribution

$$ Pr{X = x_{i}} = p_{i}, i = 1,2,..., $$
Cumulative distribution function (CDF)
$$ F_{i} = Pr{X = x_{i}} = p_{1} + p_{2} + ... + p_{i} $$

Figure 12.1

Sample nucleotide at random using probabilities 0.1, 0.2, 0.3, 0.4 for T,C,A,G respectively

```python

nucleotides = ["T","C","A","G"]
nucleotide_probabilities = [0.1,0.2,0.3,0.4]
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

nucleotide_probabilities = {
  "T":0.1,
  "C":0.2,
  "A":0.3,
  "G":0.4
}


```

## On your own: Write a function to generate a random sequence of DNA of length N for any given nucleotide probabilities




## Poisson distribution

Random variable $X$ is Poisson distributed with mean $λ$ if
$$ p_{x} = Pr(X = x) = \frac{e^(-λ) λ^(x) }{x!}, x =0,1 ..., $$

```python
# plot poisson distribution
```

Mean = Variance = λ = $E(X) = V(X)$



### Inversion method for generating Poisson variates with rate λ

1. Generate a random number $u$
2. Set $x=0$, $F = p = e^(λ)$
3. If $u < F$, set $X <-- x$, and stop
4. Set $p <-- pλ/(x+1)$,$F <-- F +p$, and $x <-- x + 1$. $F$ is now $F_{x+1}$
5. Go to step 3.

Here $F$ records the CDF



```python
import random
def inversion_poisson(λ):
  u = random.random()
  x = 0
  F = e ^ λ

  while True:
    if u < F:
      X = x
      return X
    else:
      p = F * λ/(x+1)
      F = F + p 
      x += 1



  # cdf = np.zeros(4)
  # cdf[0] =
  return X
```
