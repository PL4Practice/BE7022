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
     - 
  
  

