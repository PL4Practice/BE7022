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

- Test procedure

- Confidence interval

#### Paired-sample z-test ($$\[{\sigma_d}\]$$ is known)

- Test conditions

- Test procedure

- Confidence interval

#### Paired-sample t-test ($$\[{\sigma_d}\]$$ is unknown)

- Test conditions

- Test procedure

- Confidence interval

#### 2-sample (independent/separate groups)

- Test conditions

- Test procedure

- Confidence interval
  
#### 2-sample z-test ($$\[{\sigma_1}\]$$ and $$\[{\sigma_2}\]$$ are known and equal (=$$\[{\sigma_p}\]$$)

#### 2-sample Student's t-test($$\[{\sigma_1}\]$$ and $$\[{\sigma_2}\]$$ are known and equal (=$$\[{\sigma_p}\]$$)
 
 
 

  

    
    
  


    
  

