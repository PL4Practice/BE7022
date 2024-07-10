# Week 03
## Lecture 07
Probability concepts + Random variable + Binomial distribution
### Probability concepts
- **Random variable**: a numerical quantity that takes on different values depending on chance
  > - *Discrete*: a countable set of possible outcomes
  > - *Continuous*: an unbroken continuum of possible outcomes
- **Event**: an outcome r a set of outcomes
- **Probability**: the proportion of times an event is expected to occur in the population

<ins>Properties of Probabilities<ins/>

(Let A be an event...)
- 0 <= *Pr(A)* <= 1
- Sum of *Pr* = 1
- *Pr(Ā)* = 1 – *Pr(A)* (Ā: the complement of A, {not A})
- If *A* and *B* are disjoint outcomes, the *Pr*(A or B) = *Pr*(A) + *Pr*(B). *Pr*(A and B) = 0

<ins>Discrete random variable<ins/>

*Probabilty mass function(**pmf**)*: a mathematical relation that assigns probablities to all possible outcomes for discrete random variable.
> - Definitional formula for mean or expectation: $$\mu = \sum_{r} r \cdot P(X = r)$$
> - Definitional formula for variance: $$\sigma^2 = \sum_{r} (r - \mu)^2 \cdot P(X = r)$$
> - Cumulative probability: probability that X is of value r or less, i.e., *Pr*(x<=r)


X \~ B(n,p): /X follows Binomial distribution with n=4, p=0.75

*Example*: X~B(4,0.75)

<ins>Continuous random variable<ins/>

*Probabilty density function(**pdf**)*: a mathematical relation that assigns probablities to all possible outcomes for continuous random variable.

> - Because there are infinite outcomes, probabilty of an exact value is 0: *Pr*(X=x)=0
> - *pdf* come in many forms(shapes): uniform *pdf*; normal *pdf*; t *pdf*
> > i.e.: Unif(1,6); Normal(0,1); T(df=3)
> - Normal distribution/curve

*Example*: 100,000 tablets, a mean weight of 750mg & a standard deviation of 60mg --> normal curve --> weight X, infinite population 

On spaces which are continuum, probability models are specified in the form of a probability density function f(x), which has the following properties. f(x) has the following properties:
> 1. *f(x)* >= 0 for all possible values 
> 2. $$\int_{-\infty}^{\infty} f(x) \, dx = 1$$

*Example*: Pr(730 ≤ X ≤ 735)= Probability that the value of X for a tablet drawn at random is between 730 and 735 
  
  = Area under the curve between 730 and 735 
  
  = $$\[\int_{730}^{735} f(x) \, dx\]$$
  
  = Proportion of tablets with weights between 730 and 735.

  ### Binomial Distribution
  (Most common discrete distribution)

- Binomial – a family of discrete distributions. 
- Binomial random variable – the random number of successes in n independent *Bernoulli* (“success” or “failure”) trials.  Each of the trials produces independent results, unaffected by any previous trial.  
(Outcomes of trials involving more than 2 outcomes can be collapsed to 2 levels as success and failure based on our interest.)

Bionomial random variables have two parameters:
> n - number of trials (fixed)
> p - probability of success of each trial (constant)

If X is a binomial random variable with parameters n and p, the formula for bionomial probability of r success is:
$$\Pr(X = r) = \binom{n}{r} p^r (1 - p)^{n - r}$$

where, 

r = 0, 1, 2, … , n

$$\binom{n}{r}$$

= the binomial coefficient

= $$\frac{n!}{r!(n-r)!}$$

The expected value (mean) of a binomial random variable is ***μ*=np** and its variance is **σ^2=np(1-p)<ins/>**

When n in binomial distribution is large, we can use shortcuts to avoid tedious manual calculations.
- Use shortcuts Pr(X ≤ a) = 1 – Pr(X > a) and Pr(X < a) = 1 – Pr(X ≥ a), when a is closer to n than to 0.
- Use shortcuts Pr(X ≥ a) = 1 – Pr(X < a) and Pr(X > a) = 1 – Pr(X ≤ a), when a is closer to 0 than to n. 

*Example*:
Let X\~B(n=30, p=0.60), Pr(x<= 28)=1-Pr(X>28)=1-\[Pr(x=29)+Pr(x=30)]


The function `dbinom()` calculates the binomial probabolity.

```
> # Example: Let X ~ B(n=4, p=0.75)
> # Pr(X = r), r=0, 1, 2, 3, 4 can be calculated as
> dbinom(0, 4, 0.75)
[1] 0.00390625
> dbinom(1, 4, 0.75)
[1] 0.046875
> dbinom(2, 4, 0.75)
[1] 0.2109375
> dbinom(3, 4, 0.75)
[1] 0.421875
> dbinom(4, 4, 0.75)
[1] 0.3164063

 # Example: Let X ~ B(n=30, p=0.60)
> # Pr(x<= 28) can be calculated as:
> # Loop method
> # Loop
> sum_prob = 0
> for (i in (0:28))
+   {
+     sum_prob = sum_prob + dbinom(i, 30, 0.60)
+ }
> sum_prob
[1] 0.9999954
> # equivalently
> sum(dbinom(0:28, 30, 0.60))
[1] 0.9999954
```
Pr(X <= 28) can also be calculated as [1 - Pr(X > 28)]
```
> # equivalently
> 1 - sum(dbinom(29:30, 30, 0.60))
[1] 0.9999954
```
```
> # Pr(X < 28) can be calculated as
> sum(dbinom(0:27, 30, 0.60))
[1] 0.9999526
> # Pr(X >= 8) can be calculated as
> sum(dbinom(8:30, 30, 0.60))
[1] 0.9999507
> # Pr(X >= 8) can also be calculated as [1 - Pr(X < 8)]
> 1 - sum(dbinom(0:7, 30, 0.60))
[1] 0.9999507
> # Pr(X > 8) can be calculated as
> sum(dbinom(9:30, 30, 0.60))
[1] 0.9997777
> # Pr(X > 8) can also be calculated as [1 - Pr(X <= 8)]
> 1-sum(dbinom(0:8, 30, 0.60))
[1] 0.9997777
```
---
## Lecture 08
Normal distribution
### Normal Distribution
  (Most common continuous distribution)

- Normal – a family of continuous distributions. 
- Normal distribution is identified by parameters ***μ*** (mean) and ***σ*** (standard deviation)
- Normal distribution is bell shaped, symmetric and centered on the mean(μ)
- μ is called the mean of the distribution; and σ is called the standard deviation of the distribution
- A normal distribution is described by the following probability density function:

$$\[
f(x) = \frac{1}{\sqrt{2 \pi \sigma^2}} e^{-\frac{(x - \mu)^2}{2 \sigma^2}}
\]$$

where, e = 2.71728, pi = 3.14159

The random variable is said to follow a normal distribution with parameter μ and σ, i.e. X\~N(μ,σ).
(Once the values of μ and σ are specified, the probability density function *f(x)* can be graphed to obtain the corresponding normal curve.

In the make-up of the normal curve:
- μ controls location, the mean μ specifies the central location of the distribution;
- σ controls spread

Features of the graph of a normal density function(i.e. the normal curve) are:
> 1.	The curve is bell-shaped.
> 2.	The peak is at μ. 
> 3.	The curve is symmetrical around μ.
> 4.	The shape of the curve to the left of μ is a mirror image of the shape of the curve to the right of μ.
> 5.	<ins>The total area under the curve is one.<ins/> 
> 6.	The area under the curve to the right of μ  is 0.5.
> > 3 sigma rule/ 68-95-99.7 rule
> 7.	The area under the curve between μ - 1σ  and μ + 1σ  is 0.6826, 	i.e., 68% approximately.   
> 8.	The area under the curve between μ - 2σ  and μ + 2σ  is 0.9544, 	i.e., 95% approximately.
> 9.	The area under the curve between μ - 3σ  and μ + 3σ  is 0.9974, 	i.e., 99.7% approximately.
> 10.	The curve does not touch the X-axis.

*Example*: 

The random variable X\~N(μ=750, σ=60), and the corresponding normal distribution or normal curve:
$$\[
f(x) = \frac{1}{\sqrt{2 \pi (60)^2}} e^{-\frac{(x - 750)^2}{2 (60)^2}}
\]$$

The function *dnorm()* in R to obtain the value of the probability density function of a normal distribution for a specific value of x.
```
> # Example: X~N(μ=750, σ=60)
> ?dnorm()
> dnorm(650, mean=750, sd=60)
[1] 0.001657952
> dnorm(800, mean=750, sd=60)
[1] 0.004698531
```
Use the function *dnrom()* with the function *curve()* to plot the the normal curve.
```
> # Plot the normal curve of X~N(μ=750, σ=60)
> ?curve
> curve(dnorm(x, mean=750, sd=60), from=750-4*60, to=750+4*60, main="Normal curve of weight", xlab="x", ylab="Density")
```
<ins>68-96-99.7 rule for normal distribution<ins/>

If X is a normal random variable with parameters μ (mean) and σ (standard deviation), the 68-95-99.7 rule for normal distribution states that 
- 68% of the observations fall within ±1σ of μ,	i.e., in the interval (μ - 1σ, μ + 1σ)
- 95% of the observations fall within ±2σ of μ, 	i.e., in the interval (μ - 2σ, μ + 2σ) 
- 99.7% of the observations fall within ±3σ of μ, 	i.e., in the interval (μ - 3σ, μ + 3σ) 

<ins>Symmetry in the tails of Normal distribution<ins/>

<ins>Manually calculating Normal Probabilities<ins/>

To determine a Normal probability when the value does not fall directly on a ±1σ, ±2σ, or ±3σ landmark, 

1. State the problem
2. Standardize the value (z score described below)
3. Sketch and shade the curve 
4. Use the standard normal table to determine the probability

<ins>Standard Normal(Z) Variable<ins/>

- Standard Normal variable – a Normal random variable with μ = 0 and σ = 1
- Called “Z variable”
- Notation: Z\~N(0,1)
- Use the standard normal table to look up cumulative probabilities associated with Z ~ N(0,1).

To standardize the value x from a normal variable X\~N(μ,σ) to a z score from a standard normal variable Z\~N(0,1), substract μ and divide by σ:

$$
\[
z = \frac{x - \mu}{\sigma}
\]
$$

<ins>Probabilities between two points<ins/>
(a: represent the lower boundary; b: represent the upper boundary of a range of interest)

Pr(a <= Z <= b)

The function *pnorm()* calculates the probabilities associated with a normal curve.
> - With the default option of lower.tail=TRUE, it calculates the cumulative probability *Pr*(X <= x);
> - With the default option of lower.tail=FALSE, it calculates the cumulative probability *Pr*(X > x);
> - If the mean, μ, or sd, σ, are not specified they assume the default values of 0 and 1, respectively

```
> # To calculate Pr(730 <= x <= 735) = Pr(x <= 735) - Pr(x <= 730)
> ?pnorm
> pnorm(735, mean=750, sd=60, lower.tail=TRUE) - pnorm(730, mean=750, sd=60, lower.tail=TRUE)
[1] 0.03185233
> # To calculate Pr(X ≤ 650)
> pnorm(650, mean=750, sd=60, lower.tail=TRUE)
[1] 0.04779035
> # To calculate Pr(X > 900)
> pnorm(900, mean=750, sd=60, lower.tail=FALSE)
[1] 0.006209665
> # equivalently
> 1 - pnorm(900, mean=750, sd=60, lower.tail=TRUE)
[1] 0.006209665
```
*Example*: X~N(1076.80, 105.76)
```
> # To calculate Pr(X<=800)
> pnorm(800, mean=1076.80, sd=105.76, lower.tail=TRUE)
[1] 0.004432114
> # To calculate Pr(X<=1300)
> pnorm(1300, mean=1076.80, sd=105.76, lower.tail=TRUE)
[1] 0.9825897
```
*Example*: X~N(1520.0, 100.70)
```
> # To calculate Pr(X<=800)
> pnorm(800, mean=1520, sd=100.70, lower.tail=TRUE)
[1] 4.340465e-13
> # To calculate Pr(X<=1300)
> pnorm(1300, mean=1520, sd=100.70, lower.tail=TRUE)
[1] 0.01445517
```

