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

- sample mean: $$\[\bar{X} = \frac{1}{n} \sum_{i=1}^{n} X_i\]$$

- sample variance: $$\[s^2 = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X})^2\]$$
  
- sample standard deviation: $$\[s = \sqrt{s^2}\]$$

When X is Normal or for a large sample (n >= 30) from any distribution, $$\[\bar{x} \sim \mathcal{N}(\mu, SE_\bar{x}\]$$, where, the standard deviation of $$\[\bar{x}\]$$ is:
$$\[\sigma_{\bar{X}} = SE_{\bar{X}} = \frac{\sigma}{\sqrt{n}}\]$$


<ins> Sample types for testing/inferences on means<ins/>

- a) 1-sample: One group; no concurrent control group, comparisons made to external population.
  > i.e. Measure vutamin content in loaves of bread and see if the average meets national standards
- b) Paired-sampe: Two samples with each data point in one sample uniquely matched to a point in the other; (consider as a single smaple of - paired differences and analyze within-pair differences)
  > i.e. Compare vitamin content of bread loaves immediately after baking versus vitamin content in the same loaves 3 days later.
- c) 2-sample： Two independent/separate groups; no matching or pairing; compare separate groups. (A single sample can be grouped by 2 levels of a variable and the resulting 2 groups will be considered as two independent samples.)
  > i.e. Compare vitamin content of bread immediately after baking versus other loaves that have been on shelf for 3 days

### Hypothesis Testing
  *Hypothesis testing* is also called *significance testing*. The objective of hypothesis testing is to test claims about parameters.

<ins>STEPS<ins/>:
- a. State null and alternative hypotheses and fig significance level. [NULL hypothesis: $$\[H_0\]$$, alternative hypotheses: $$[H_1\]$$
- b. Calculate test statistic (based on null hypothesis value forparameter.)
- c. Calculate *p*-value for the test statistic.
- d. Reject null hypothesis if *p*-value <= significance level. Retain null hypothesis if *p* value > significance level.
  > While hypothesis testing is applicable to many parameters (involving different distributions and populations), this illustrative description focuses on testing the population mean µ using information from a single sample.

<ins>Null and alternative hypotheses<ins/>:
- The null hypothesis ($$\[H_0\]$$): a claim of "no difference in the population". ($$\[H_0: \mu = {\mu_0}\]$$)
- - The alternative hypothesis ($$\[H_a\]$$: a claim of "difference".
       * One-sided alternatives ($$\[H_a:\mu > {\mu_0}\]$$, $$\[H_a:\mu < {\mu_0}\]$$)
       * Two-sided alternatives ($$\[H_a:\mu \neq {\mu_0}\]$$)

  <ins>Significance level (α)<ins/>:
  - Let α represent the probability of erroneously rejecting $$\[H_0\]$$.
  - Set α threshold of acceptable error (e.g., α = 0.10 or α = 0.05, or whatever level is acceptable).
  - α = 0.05 is most common.
    > Rigorous tests involve α = 0.01 while lenient tests involve α = 0.10


  <ins>Test statistic<ins/>:
  - The z statistic for one-sample problems about means.
    $$\[\mathcal{Z_stat} = \frac{\bar{x} - {\mu_0}}{\frac{\sigma}{\sqrt{n}}} \sim \mathcal{N}(0,1)\]$$

  <ins>*p*-value<ins/>:
  - The probability that test statistic is more extreme than the observed value, assuming $$\[H_0\]$$ is true.
  - This corresponds to the area in the tail of the Z sampling distribution beyond the observed $$\[\mathcal{Z_stat}\]$$.
  - Smaller *p*-values provide stronger evidence aganinst $$\[H_0\]$$.
    * For two-sided $$\[H_a\]$$ --> consider "up" and "down" deviations
      - Two-tailed test considers the possibility of relationship in both directions.
      > double the one-sided *p*-value

    * For one-sided $$\[H_a\]$$ --> use the area in the tail beyond the observed z statistic
      - One-tailed test considers the possibility of relationship in one direction and completely disregards the possibility of a relationship in the other direction.
      > hence, a one-tailed test is not common and used in specific situations only
      > 
      > i. For $$\[H_a: \mu < {\mu_o}\]$$, use area to left of observed $$\[\mathcal{Z_stat}$$
      > 
      > ii. For $$\[H_a: \mu > {\mu_o}\]$$, use area to right of observed $$\[\mathcal{Z_stat}$$
      > 
      > i.e. In testing this drug, you are only interested in testing if it less effective than the existing drug.  You do not care if it is significantly more effective.  You only wish to show that it is not less effective. In this scenario, a one-tailed test.

---
 
#### 1-sample z-test ($$\[{\sigma}\]$$ is known)

- Test conditions
  * Continuous variable X, simple random sample, σ is known
  * X is approximately Normal (any *n*) or n >= 30 from any distribution
- Test procedure
  * A. Formulate $$\[H_O: \mu = {\mu_0}\]$$ versus $$\( H_a: \mu \neq \mu_0 \)$$ ( <>)
  * B. Choose significance level α (ussually 0.05 or 0.01)
  * C. Test statistic $$\[ \mathcal{Z}_{\text{sat}} = \frac{\bar{x} - \mu_0}{\frac{\sigma}{\sqrt{n}}} \sim \mathcal{N}(0, 1) \]$$
  * D. (Calculate *p*-value using R)
  * E. Reject $$\[H_O\]$$ if *p*-value < α
- Confidence interval
  A (1-α)100% confidence interval for μ is calculated as $$\[
\bar{x} \pm z_{(1-\alpha/2)} \frac{\sigma}{\sqrt{n}}\]$$ where the critical value $$\(z_{(1-\alpha/2)}\)$$ satisfies the criteria $$\[
Pr(Z \leq z_{(1-\alpha/2)}) = (1-\alpha/2) \]$$ for $$\[Z \sim \mathcal{N}(0,1)\]$$


#### 1-sample t-test ($$\[{\sigma}\]$$ is unknown)

- Test conditions
  * Continuous variable X, simple random sample, σ is unknown (estimated using s)
  * X is approximately Normal (any *n*) or n >= 30 from any distribution
- Test procedure
  * A. Formulate $$\[H_O: \mu = {\mu_0}\]$$ versus $$\( H_a: \mu \neq \mu_0 \)$$ ( <>)
  * B. Choose significance level α (ussually 0.05 or 0.01)
  * C. Test statistic $$\[t_{\text{stat}} = \frac{\bar{x} - \mu_0}{\frac{s}{\sqrt{n}}} \sim t_{(n-1)}.\]$$
  * D. (Calculate *p*-value using R)
  * E. Reject $$\[H_O\]$$ if *p*-value < α
    
- Confidence interval


#### Paired-sample z-test ($$\[{\sigma_d}\]$$ is known)
Each point in one sample is matched to a unique point in the other sample.
  > Example: Pre- and post-intervention values, different time points
  > 
  > Xd,i = X1,i – X2,i

- Test conditions
  * Continuous variable $$\[X_{d,i}\]$$, simple random sample, σ is unknown (estimated using $${s_d}$$)
  * X is approximately Normal (any *n*) or n >= 30 from any distribution



- Test procedure

- Confidence interval

#### Paired-sample t-test ($$\[{\sigma_d}\]$$ is unknown)

- Test conditions

- Test procedure

- Confidence interval

#### 2-sample (independent/separate groups)

Notations in 2 samples:

Population parameters 
|   | Size | Mean | SD |
|---|---|---|---|
| Group 1 | N1 | µ1 | σ1 |
| Group 2	| N1 | µ2 | σ2 |

Sample statistics
|    |Size | Mean | SD |
|---|---|---|---|
| Group 1 |	n1 | x ̅_1 |	s1 | 
| Group 2	| n2 | x ̅_2	| s2 |

Test/inferences on (µ1 – µ2) using difference of means = $$\[\bar{x_1} - \bar{x_2}\]$$
Standard error of difference of means quantifies how precisely $$\[\bar{x_1} - \bar{x_2}\]$$ estimates $$\[\bar{\mu_1} - \bar{\mu_2}\]$$

- Test conditions



- Test procedure

- Confidence interval
  
#### 2-sample z-test ($$\[{\sigma_1}\]$$ and $$\[{\sigma_2}\]$$ are known and equal (=$$\[{\sigma_p}\]$$)

#### 2-sample Student's t-test($$\[{\sigma_1}\]$$ and $$\[{\sigma_2}\]$$ are known and equal (=$$\[{\sigma_p}\]$$)


---
## Lecture 12
Examples of tests on 1-sample, paired-smaple and 2-sample means + and Confidence Intervals
### 1-sample z-test ($$\[{\sigma}\]$$ is known)
Example 1
```
> # Example 1
> # Weschler Adult Intelligence Scores are Normal with mu = 100 and sigma = 15
> # Take an SRS of n = 9
> # Measure scores: {116, 128, 125, 119, 89, 99, 105, 116, 118}
> # Does this sample mean provide statistically reliable evidence that population mean μ is > than 100? 
> # Intelligence score: X ~ N(μ = 100, sigma = 15)
> # X ~ N.  Normality requirement of x ̅ is satisfied.
> # H0: μ = 100 versus Ha: μ > 100

> Scores = c(116, 128, 125, 119, 89, 99, 105, 116, 118)
> alpha = 0.05
> x_bar = mean(Scores)
> mu_0 = 100
> sigma = 15
> n = length(Scores)
```
1-sample z-test is not available in base R. Let's build an user-defined function for it.
#### Create R function
```
# Create R function

# Basic functions
my_function <- function() { # create a function with the name my_function
  print("test my function")
}

# Call a function
my_function() # call the function named my_function


# Nested Functions
Nested_function <- function(x, y) {
  a <- x + y
  return(a)
}
Nested_function(Nested_function(2,2), Nested_function(3,3))

## a function within a function:
Outer_func <- function(x) {
  Inner_func <- function(y) {
    a <- x + y
    return(a)
  }
  return (Inner_func)
}
output <- Outer_func(3) # To call the Outer_func
output(5)

## R Function Recursion
tri_recursion <- function(k) {
  if (k > 0) {
    result <- k + tri_recursion(k - 1)
    print(result)
  } else {
    result = 0
    return(result)
  }
}
tri_recursion(6)
```
In this case:
```
# Create onesample.ztest function
onesample.ztest = function(x_bar, mu_0, sigma, n){
  one.z.stat = (x_bar - mu_0) / (sigma/sqrt(n))
  
  pvalue_twosided = 2 * pnorm(-abs(one.z.stat), mean=0, sd=1, lower.tail=TRUE)
  pvalue_less = pnorm(one.z.stat, mean=0, sd=1, lower.tail=TRUE)
  pvalue_greater = 1 - pnorm(one.z.stat, mean=0, sd=1, lower.tail=TRUE) 
  
  output = list (
    paste("one.z.stat =", round(one.z.stat, 4)),
    paste("pvalue_twosided =", round(pvalue_twosided, 4)),
    paste("pvalue_less =", round(pvalue_less, 4)),
    paste("pvalue_greater =", round(pvalue_greater, 4))
  )
  return(output)
}
```
Call user-defined onsample.ztest() function.
```
> onesample.ztest(x_bar=x_bar, mu_0=mu_0, sigma=sigma, n=n)
[[1]]
[1] "one.z.stat = 2.5556"

[[2]]
[1] "pvalue_twosided = 0.0106"

[[3]]
[1] "pvalue_less = 0.9947"

[[4]]
[1] "pvalue_greater = 0.0053"

> mean(Scores)
[1] 112.7778
# onesamole.ztest(112.7778, 200, 15, 9)
# Reject the null hypothesis as the one-sided p-value = 0.0053 < alpha = 0.05.  Conclude that the mean adult intelligence score is > 100.
```
Example 2
In the 1970s, 20–29 year old men in the U.S. had a mean body weight μ of 170 pounds. Standard deviation σ = 40 pounds. We want to test whether mean body weight in the population now differs.
- Take an SRS of n = 64
- Let sample mean = 173
- Does this sample mean provide statistically reliable evidence that population mean body weight of 20–29 year old men in the U.S. has changed since the 1970s? 

```
> # Example 2
> # Current body weight: X~(mu,40), mu(unknown)
> # Distribution of X is unknown
> # n = 64(>=30), Normality requirement of x_bar is satisfied
> # H0: mu =170 versus Ha:mu no equal 170
> onesample.ztest(x_bar = 173, mu_0 = 170, sigma = 40, n = 64)
[[1]]
[1] "one.z.stat = 0.6"

[[2]]
[1] "pvalue_twosided = 0.5485"

[[3]]
[1] "pvalue_less = 0.7257"

[[4]]
[1] "pvalue_greater = 0.2743"
# Do not reject null hyothesis as the two-sided p-value = 0.5485 > alpha = 0.005. Insufficient evidence to conclude that current mean body weight is not equal 170. Mean body weight of 20–29 year old men in the U.S. has not changed since the 1970s. 
```

 

  

    
    
  


    
  

