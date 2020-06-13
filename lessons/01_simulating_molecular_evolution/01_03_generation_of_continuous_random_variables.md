# Module 1, Lesson 3: Generation of continuous random variables


## To be covered in slides
* Memorylessness

<!-- ## The inversion method

### Uniform distribution

Generate a random variable from the uniform distribution x ~ U(a,b).

CDF F(x) = (x-a)/(b-a)
u = (x-a)/(b-a) is a U(0,1) random number.
Generate u ~ U(0,1)
obtain x, x = a + u(b-a)

```python
u = (x-a)/(b-a)
x = a + u*(b-a)
``` -->

### exponential distribution


$$f(x) = \frac{1}{\theta}e^{\frac{-x}{\theta}}$$
```python
def exponential_n(x,theta):
  y = (1/theta) * np.exp(-x/theta)

plot(exponential_n)
```

```python
numpy.random.exponential()
```


<!-- ## Generation of a standard normal variate using the polar method

Equation 12.18
Equation 12.19



### Polar method to generate normal variates x,y ~ N(0,1)

Step 1. Generate a random point (v1,v2) within unit circle

  a. Generate u1,u2 ~ U(0,1)
  b. Set v1 <- 2(u1) -1, v2  <- 2(u2)
  c. if s = v1^2 +v2^2 > 1, go back to 1a

Step 2. Set x = √-2log(s) * v1 / √s = √-2log(s)/s * v1 and y = √-2log(s)/s*v2 -->
## Gamma, beta, and Dirichlet variables

<!-- `Does every site in the sequence evolve at the same rate? Probably not. This feature of gene evolution is often approximated using the gamma distribution. The idea is that there is a probability that any site will evolve at a given rate and that probability is drawn from the gamma distribution. For each site, the likelihood is calculated for every possible rate; the likelihood under each rate is multiplied by the probability of that rate under the gamma distribution; and all those likelihoods are added together to calculate the total likelihood for the site` -->

```python

numpy.random.gamma()
numpy.random.beta()
numpy.random.dirichlet()

```

### gamma
$$f(x;\alpha,\beta) = \frac{\beta^{\alpha}}{\Gamma(\alpha)}*e^{-\beta * x}* x^{\alpha -1}, \alpha > 0,\beta > 0, x > 0$$

$$ \Gamma (\alpha)=(\alpha-1)!$$

## beta
$$ f(x; p,q) = \frac{1}{B(p,q)} * x^{p-1}(1-x)^{q-1}, 0 <x<1,p>0,q>0  $$

$$ B(p,q)  = \frac{\Gamma(p)\Gamma(q)}{\Gamma(p + q)}$$

### dirichlet

$$f(x; a_1,a_2,...,a_{\Kappa}) = \frac{\Gamma(\alpha)}{\prod_{i=1}^{Kappa}\Gamma(\alpha_{i})} \prod_{i=1}^{Kappa} x_i^{a_i -1},a_i > 0 $$



Go over equations and numpy or scipy functions that generate these

```python
import numpy
import scipy
```


rnorm,rgamma,rbeta in R. Not sure in python??
