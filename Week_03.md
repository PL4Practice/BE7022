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


