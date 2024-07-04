# Week 02
## Lecture 03
Data summarization using **tabular methods** (descriptive statistics): Tabular analysis of **Prostate.xlsx* data.
> **Recap**:
> 
> *Type of statistics*
> 1. Descriptive statistics
> 2. Inferential statistics
>
> *Type of variables*
> 1. Categorical variable
> 2. Continuous variable
---
**Tabular descriptive statistics on categorical variables:**
> •	Categories can be arranged in any order.
> 
> •	Mathematical/arithmetic operations are not meaningful.
> 
> •	Allowable calculations are count (*frequency*) and *proportions* (%s) of categories.


- Single categorical variable can be summarized using:
  > - Frequency table
  > - Relative frequency table

- Two categorical variables can be summarized using:
  > - Contingency table (cross-tabulation)
  > > presents the count (frequency) and proportions of 2 categorical variables in a row X column format.
---
**Tabular descriptive statistics on continuous variables:**

Mathematical/arithmetic operations are not meaningful.

- Single continuous variable can be summarized using:

> Summary descriptive statistics

- **Center Location** (Center of the variable)
  - Mean          - Average value
  - Median(Q2)    - Middle value (50th percentile)
  - Mode          - Most frequent value
> The mean is the traditional measure of central location.  The median is more resistant to skews and outliers than the mean; it is more robust.  The mode is useful only in large data sets with repeating values.


- **Variability** (Spread or Dispersion of the variable)
  - Minimum       - Min value
  - Q1            - First quartile (25th percentile)
  - Q3            - Third quartile (75th percentile)
  - Maximum       - Max value
  - Range         - Max-Min
  - Inter-Quartile Range (IQR)         - Q3-Q1
  - Variance      - A collective measure of the distances between the individual values and the mean
  - Standard Deviation   - Square-root of the variance
    > The standard deviation is the most common descriptive measure of variability and is based on deviations around the mean.  Always report a measure of central location, a measure of spread, and the sample size.
  
   * Report (mean ± standard deviation) for symmetrical mound-shaped distributions.
   * Report (min., Q1, median, Q3, max.) or (median and IQR) for odd shaped distributions.

Distribution:
1. mean = median >>> *symmetrical*
2. mean > median >>> *positive skew*
3. mean < median >>> *negative skew*

---

- Two continuous variable can be summarized using:
  - Correlation co-efficient
    - he correlation co-efficient (ρ or r) describes the direction and <ins>strength</ins> of <ins>linear relationship</ins> between the 2 continuous variables.
    - 1 <= r <= 1
    - "-ve" value: a decreasing relationship; strong when close to -1.
    - value close to 0 indicates independence between 2 variables.
    - "+ve" value: a increasing relationship; strong when close to 1.
    - *Pearson correlation coefficient*: parametric, value-based
    - *Spearman correlation coeffient*: nonparametric, rank-based
---
CASE: Tabular analysis of Prostate.xlsx
```

> # Import the data into R
> library('openxlsx')
> # Examine structure and dimension of data
> str(Prostate)
'data.frame':	502 obs. of  18 variables:
 $ patno : num  1 2 3 4 5 6 7 8 9 10 ...
 $ stage : num  3 3 3 3 3 3 3 3 3 3 ...
 $ rx    : chr  "0.2 mg estrogen" "0.2 mg estrogen" "5.0 mg estrogen" "0.2 mg estrogen" ...
 $ dtime : num  72 1 40 20 65 24 46 62 61 60 ...
 $ status: chr  "alive" "dead - other ca" "dead - cerebrovascular" "dead - cerebrovascular" ...
 $ age   : num  75 54 69 75 67 71 75 73 60 78 ...
 $ wt    : num  76 116 102 94 99 98 100 114 110 107 ...
 $ pf    : chr  "normal activity" "normal activity" "normal activity" "in bed < 50% daytime" ...
 $ hx    : num  0 0 1 1 0 0 0 1 0 1 ...
 $ sbp   : num  15 13 14 14 17 19 14 17 12 13 ...
 $ dbp   : num  9 7 8 7 10 10 10 11 8 8 ...
 $ ekg   : chr  "heart strain" "heart block or conduction def" "heart strain" "benign" ...
 $ hg    : num  13.8 14.6 13.4 17.6 13.4 ...
 $ sz    : num  2 42 3 4 34 10 13 3 4 21 ...
 $ sg    : num  8 NA 9 8 8 11 9 9 10 6 ...
 $ ap    : num  0.3 0.7 0.3 0.9 0.5 ...
 $ bm    : num  0 0 0 0 0 0 0 0 0 0 ...
 $ sdate : num  2778 2820 2933 2999 3002 ...
> dim(Prostate)
[1] 502  18
```
Let's summarizing the **categorical variables** *rx* and status. 
> rx: treatment ( placebo, 0.2/1.0/5.0 mg estrogen)
```
> # create factor variabble rx_f and status_f from the charactor variables rx and status
> Prostate$rx_f = factor(Prostate$rx)
> Prostate$status_f = factor(Prostate$status)
> # Obtain frequency tables(counts) of rx_f and status_f
> table(Prostate$rx_f)

0.2 mg estrogen 1.0 mg estrogen 5.0 mg estrogen         placebo 
            124             126             125             127 
> table(Prostate$status_f)

                       alive       dead - cerebrovascular 
                         148                           31 
    dead - heart or vascular              dead - other ca 
                          96                           25 
dead - other specific non-ca          dead - prostatic ca 
                          28                          130 
    dead - pulmonary embolus   dead - respiratory disease 
                          14                           16 
        dead - unknown cause    dead - unspecified non-ca 
                           7                            7
> prop.table(table(Prostate$rx_f))

0.2 mg estrogen 1.0 mg estrogen 5.0 mg estrogen         placebo 
       0.247012        0.250996        0.249004        0.252988 
> prop.table(table(Prostate$status_f))

                       alive       dead - cerebrovascular 
                  0.29482072                   0.06175299 
    dead - heart or vascular              dead - other ca 
                  0.19123506                   0.04980080 
dead - other specific non-ca          dead - prostatic ca 
                  0.05577689                   0.25896414 
    dead - pulmonary embolus   dead - respiratory disease 
                  0.02788845                   0.03187251 
        dead - unknown cause    dead - unspecified non-ca 
                  0.01394422                   0.01394422
```
```
# Create the character variable 'died' from the character variable 'status'
> for (i in (1:502))
+ { if (Prostate$status[i] == "alive")
+     {
+         Prostate$died[i] = "No"
+     }
+     else
+     {
+         Prostate$died[i] = "Yes"
+     }
+ }

> # Create the factor variable died_f from the character variable died
> Prostate$died_f = factor(Prostate$died)
> # Obtain cross-tabulation (with counts) of rx_f and died_f ('rx', treatment)
> table(Prostate$rx_f, Prostate$died_f)
                 
                  No Yes
  0.2 mg estrogen 29  95
  1.0 mg estrogen 55  71
  5.0 mg estrogen 32  93
  placebo         32  95

> # Obtain cross-tabulation (with cell proportions) of rx_f and died_f
> # "Cell proportions" in the context of a cross-tabulation or contingency table refer to the relative frequencies of each cell in the table compared to the total number of observations.
> prop.table(table(Prostate$rx_f, Prostate$died_f))
                 
                          No        Yes
  0.2 mg estrogen 0.05776892 0.18924303
  1.0 mg estrogen 0.10956175 0.14143426
  5.0 mg estrogen 0.06374502 0.18525896
  placebo         0.06374502 0.18924303

> # Obtain relative frequency tables (with row proportions) of rx_f and died_f.
> prop.table(table(Prostate$rx_f, Prostate$died_f), 1)
                 
                         No       Yes
  0.2 mg estrogen 0.2338710 0.7661290
  1.0 mg estrogen 0.4365079 0.5634921
  5.0 mg estrogen 0.2560000 0.7440000
  placebo         0.2519685 0.7480315
# "Row proportions" in the context of a cross-tabulation or contingency table refer to the relative frequencies of each cell within a row, compared to the total number of observations in that row.
> # Obtain relative frequency tables (with column  proportions) of rx_f and died_f.
> prop.table(table(Prostate$rx_f, Prostate$died_f), 2)
                 
                         No       Yes
  0.2 mg estrogen 0.1959459 0.2683616
  1.0 mg estrogen 0.3716216 0.2005650
  5.0 mg estrogen 0.2162162 0.2627119
  placebo         0.2162162 0.2683616
> ?prop.table
> prop.table(table(Prostate$rx_f, Prostate$died_f), margin = 2)
                 
                         No       Yes
  0.2 mg estrogen 0.1959459 0.2683616
  1.0 mg estrogen 0.3716216 0.2005650
  5.0 mg estrogen 0.2162162 0.2627119
  placebo         0.2162162 0.2683616
```
Next, let's consider summarizing the **continuous variables**: age, wt, sbp, dbp, hg, sz, and sg.
```
> summary(Prostate$age)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
  48.00   70.00   73.00   71.46   76.00   89.00       1 
> summary(Prostate$wt)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
  69.00   90.00   98.00   99.03  107.00  152.00       2 
> summary(Prostate$sbp)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
   8.00   13.00   14.00   14.35   16.00   30.00 
> summary(Prostate$dbp)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  4.000   7.000   8.000   8.149   9.000  18.000 
> summary(Prostate$hg)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  5.899  12.299  13.699  13.446  14.699  21.199 
> summary(Prostate$sz)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
   0.00    5.00   11.00   14.63   21.00   69.00       5 
> summary(Prostate$sg)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
   5.00    9.00   10.00   10.31   11.00   15.00      11 
```
The summary() function did not ptovide the mode, variance...
```
> # Using the pkg 'Hmisc'
> install.packages('Hmisc')
> library('Hmisc')
> help("describe", package = 'Hmisc')
> describe(Prostate$age)
Prostate$age 
       n  missing distinct     Info     Mean      Gmd      .05      .10      .25 
     501        1       41    0.996    71.46    7.497       56       60       70 
     .50      .75      .90      .95 
      73       76       78       80 

lowest : 48 49 50 51 52, highest: 84 85 87 88 89
# This did not provide the mode, variance and standard deviation measures too.
# Try ‘bystats’ in ‘Hmisc‘
> help("bystats", package = 'Hmisc')
> bystats(Prostate$age)
Error in interaction(..., drop = TRUE, sep = " ") : No factors specified
> bystats(Prostate$age, 0)

 Mean of Prostate$age by  

      N Missing     Mean
0   501       1 71.45709
ALL 501       1 71.45709
# Technically, the bystats() functions provides statistics on a single continuous variable by levels of a factor. However, you can try tricking it with the value 0 instead of a factor.

# Customized
> bystats(Prostate$age, 0, fun=function(x) c(Mean=mean(x), Median=median(x), Mode=mode(x), SD=sd(x), quantile(x)))

 c(1, 30, 1, 111, 30, 111, 1, 1) of Prostate$age by 0 

    N     Missing Mean               Median Mode      SD                0%  
0   "501" "1"     "71.4570858283433" "73"   "numeric" "7.0812890557171" "48"
ALL "501" "1"     "71.4570858283433" "73"   "numeric" "7.0812890557171" "48"
    25%  50%  75%  100%
0   "70" "73" "76" "89"
ALL "70" "73" "76" "89"
Warning message:
In formals(fun) : argument is not a function
# same as othe variables

```
Lastly, let's look at the correlations between the continuous variables age, wt, sbp, dbp, hg, sz, and sg.

The 'cor()' function can be used to calculate the correlation matrix of a dataframe or a numeric matrix.
```
> # Create a subset dataframe with only the continuous variables of interest.
> Prostate_ContinuousVars = subset(Prostate, select=c(age, wt, sbp, dbp, hg, sz, sg))
> # Obtain the Pearson and Spearman correlation matrices using cor() function with 'complete.obs' option to remove rows with missing data for any of the continuous variables selected.
> ?cor
> cor_pearson = cor(Prostate_ContinuousVars, method=c("pearson"), use="complete.obs")
> cor_spearman = cor(Prostate_ContinuousVars, method=c("spearman"), use="complete.obs")
> # Use the round() function on the output of the cor() function to round the result to 2 decimal places.
> round(cor_pearson, 2)
      age    wt   sbp   dbp    hg    sz    sg
age  1.00 -0.06  0.10 -0.07 -0.09  0.01 -0.06
wt  -0.06  1.00  0.21  0.23  0.26 -0.05 -0.09
sbp  0.10  0.21  1.00  0.63  0.06  0.05 -0.03
dbp -0.07  0.23  0.63  1.00  0.15 -0.04 -0.07
hg  -0.09  0.26  0.06  0.15  1.00 -0.13 -0.14
sz   0.01 -0.05  0.05 -0.04 -0.13  1.00  0.38
sg  -0.06 -0.09 -0.03 -0.07 -0.14  0.38  1.00
> round(cor_spearman, 2)
      age    wt   sbp   dbp    hg    sz    sg
age  1.00 -0.03  0.07 -0.10 -0.13 -0.03 -0.03
wt  -0.03  1.00  0.19  0.21  0.26 -0.01 -0.08
sbp  0.07  0.19  1.00  0.57  0.07  0.07 -0.03
dbp -0.10  0.21  0.57  1.00  0.16 -0.01 -0.05
hg  -0.13  0.26  0.07  0.16  1.00 -0.14 -0.12
sz  -0.03 -0.01  0.07 -0.01 -0.14  1.00  0.36
sg  -0.03 -0.08 -0.03 -0.05 -0.12  0.36  1.00
```
---
## Lecture 4&5 
Data summarization using **graphical methods**: Graphical analysis of **Prostate.xlsx* data.
> with functions: 'tapply()', 'bystats()', 'par()', 'plot()', 'pairs()', and 'ggplot()'

**Graphical methods on categorical variables:**
- Single categorical variable can be graphically presented using:
  - Pie chart
  - Bar chart (vertical or horizontal)
  
- Two categorical variable can be graphically presented using:
  - Clustered bar plot
    > levels of the 2nd variable are clustered/split within levels of the first variable
    > can be vertical or horizontal

**Graphical methods on continuous variables:**
- Single continuous variable can be graphically presented using:
  - Box-and-Whisker plot or Box plot
    > A box plot does not identify multimodal data, which involve 2 distinct central locations.  Histograms are better suited to identify multimodality in a variable.
  - Histogram(touching bars)
  
- Two continuous variable can be graphically presented using:
  - Correlogram
  - Scatter plot
---
