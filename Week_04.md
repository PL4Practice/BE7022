# Week 04
## Lecture 11
Student's t distribution + Hypothesis testing + Tests iin 1-sample, paired-smaple and 2-sample means + Relationship Between Hypothesis Testing and Confidence Intervals
### Student's t distribution
- A family of distribution identified by "Student" (William Sealy Gosset.
- t family members are identified by their degrees of freedom, *df*.
- t distribution are similar to z distribution but with broader tails.
- As df increases  -> t tails get tkinner -> t become more like Z~N(0,1)
  > The t ditribution becomes more like a standard distribution as the *df* increases.
  > - A t distribution with infinite *df* is a standard normal distribution.
  > - A t distribution with 60 or more *df* is indistinguished from a standard normal distribution.

### Degrees of freedom
The number of independent (i.e. free to vary) pieces of information that go into the estimate of a parameter is called the degrees of freedom (*df*).

*Example*: The sample variance s^2 (which is an estimate of the population variance σ^2) has n-1 *df*. 

In general, the degrees of  freedom of an estimate = the number of independent scores that go into the estimate - the number of parameters estimated as intermediate steps in the estimation of the parameter it self.
(or, the degrees of freedom for an estimate is equal to the number of values minus the number of parameters estimated en route to the estimate in question)


Consider a random variable with population mean *μ* and std.dev *σ*, the following scenarios:

| Intent | Approach |
|--------|---------|
| Test μ while using known σ | Z-tests |
| Test μ while using an estimate of σ | t-tests |
| Test σ | ? |

Let x1, x2, … , xn denote a sample of n observations drawn from the population.  The statistics of this sample include the following:
- sample mean
$$\[\bar{X} = \frac{1}{n} \sum_{i=1}^{n} X_i\]


- sample variance 		s^2=∑_(i=1)^n▒〖〖(x_i-x ̅)〗^2/(n-1)〗 
- sample standard deviation 	s=√(s^2 )

