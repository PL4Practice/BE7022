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




  


