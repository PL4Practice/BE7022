# Week 01
## Lecture 1
### Data structure:
| Dimension | Homogeneous | Heterogeneous |
|-----------|--------------|------------- |
| one-dimensional | Atomic Vector | List |
| two-dimensional | Matrix | Data Frame |
| multi-dimensional | Array | List |

#### Vector
A vector is an ordered/indexede sequence of values that can be of a single type:
> logical; integer; double(numeric); character; complex; raw
Individual elements of a vector are accessed using an **index**.

```
> a <- c(1,5,2,43,4,78,9,10,9,9)
> a
 [1]  1  5  2 43  4 78  9 10  9  9
> mean(a)
[1] 17
> sum(a)
[1] 170
> length(a)
[1] 10
> a+2
 [1]  3  7  4 45  6 80 11 12 11 11
> a
 [1]  1  5  2 43  4 78  9 10  9  9
> 2*a
 [1]   2  10   4  86   8 156  18  20  18  18
> a*2
 [1]   2  10   4  86   8 156  18  20  18  18
# modulo: get remainder of a division
> a%%2 
 [1] 1 1 0 1 0 0 1 0 1 1

# INDEXING
> a
 [1]  1  5  2 43  4 78  9 10  9  9
> # change the first value
> a[1]=5
> a
 [1]  5  5  2 43  4 78  9 10  9  9
> a
 [1]  5  5  2 43  4 78  9 10  9  9
> # get the 5th element of a
> a[5]
[1] 4
> # get a without 2nd element
> a[-2]
[1]  5  2 43  4 78  9 10  9  9
> # get the first 3 elements of a
> a[c(1,2,3)]
[1] 5 5 2
> a[1:3]
[1] 5 5 2
> a[2:5]
[1]  5  2 43  4

> # logical operation
> a
 [1]  5  5  2 43  4 78  9 10  9  9
> a==5
 [1]  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
[10] FALSE
> which(a==5)
[1] 1 2
> sum(a==5)
[1] 2

> # create a vector ...
> b = 1:10
> b
 [1]  1  2  3  4  5  6  7  8  9 10
> # create a vector with 10 2's
> c = rep(2,10)
> c
 [1] 2 2 2 2 2 2 2 2 2 2
> # create a vector with elements 2,4,6,8,10
> d = seq(2,10,2)
> d
[1]  2  4  6  8 10
> # create a vector by a combination of available vectors
> e = c(b,c)
> e
 [1]  1  2  3  4  5  6  7  8  9 10  2  2  2  2  2  2  2  2
[19]  2  2

> # operation between 2 vectors(of same length)
> b+c
 [1]  3  4  5  6  7  8  9 10 11 12
> b-c
 [1] -1  0  1  2  3  4  5  6  7  8
> b*c
 [1]  2  4  6  8 10 12 14 16 18 20
> b/c
 [1] 0.5 1.0 1.5 2.0 2.5 3.0 3.5 4.0 4.5 5.0

> # Element-wise operatios: max, min
> pmax(b,c)
 [1]  2  2  3  4  5  6  7  8  9 10
> b
 [1]  1  2  3  4  5  6  7  8  9 10
> c
 [1] 2 2 2 2 2 2 2 2 2 2
> pmax(b,c)
 [1]  2  2  3  4  5  6  7  8  9 10
> pmin(b,c)
 [1] 1 2 2 2 2 2 2 2 2 2

# fast
> x=(1:1e8)+(2:(1e8+1))
> head(x)
[1]  3  5  7  9 11 13
> tail(x)
[1] 199999991 199999993 199999995 199999997 199999999
[6] 200000001
```
##### Practice 1
```
> x = c(seq(1,99,2), seq(2,100,2))
> x
  [1]   1   3   5   7   9  11  13  15  17  19  21  23  25
 [14]  27  29  31  33  35  37  39  41  43  45  47  49  51
 [27]  53  55  57  59  61  63  65  67  69  71  73  75  77
 [40]  79  81  83  85  87  89  91  93  95  97  99   2   4
 [53]   6   8  10  12  14  16  18  20  22  24  26  28  30
 [66]  32  34  36  38  40  42  44  46  48  50  52  54  56
 [79]  58  60  62  64  66  68  70  72  74  76  78  80  82
 [92]  84  86  88  90  92  94  96  98 100
> y = c(rep(100,50), 1:50 )
> y
  [1] 100 100 100 100 100 100 100 100 100 100 100 100 100
 [14] 100 100 100 100 100 100 100 100 100 100 100 100 100
 [27] 100 100 100 100 100 100 100 100 100 100 100 100 100
 [40] 100 100 100 100 100 100 100 100 100 100 100   1   2
 [53]   3   4   5   6   7   8   9  10  11  12  13  14  15
 [66]  16  17  18  19  20  21  22  23  24  25  26  27  28
 [79]  29  30  31  32  33  34  35  36  37  38  39  40  41
 [92]  42  43  44  45  46  47  48  49  50
> x+y
  [1] 101 103 105 107 109 111 113 115 117 119 121 123 125
 [14] 127 129 131 133 135 137 139 141 143 145 147 149 151
 [27] 153 155 157 159 161 163 165 167 169 171 173 175 177
 [40] 179 181 183 185 187 189 191 193 195 197 199   3   6
 [53]   9  12  15  18  21  24  27  30  33  36  39  42  45
 [66]  48  51  54  57  60  63  66  69  72  75  78  81  84
 [79]  87  90  93  96  99 102 105 108 111 114 117 120 123
 [92] 126 129 132 135 138 141 144 147 150
> pmax(x,y)
  [1] 100 100 100 100 100 100 100 100 100 100 100 100 100
 [14] 100 100 100 100 100 100 100 100 100 100 100 100 100
 [27] 100 100 100 100 100 100 100 100 100 100 100 100 100
 [40] 100 100 100 100 100 100 100 100 100 100 100   2   4
 [53]   6   8  10  12  14  16  18  20  22  24  26  28  30
 [66]  32  34  36  38  40  42  44  46  48  50  52  54  56
 [79]  58  60  62  64  66  68  70  72  74  76  78  80  82
 [92]  84  86  88  90  92  94  96  98 100
> sum(x) + sum(y)
[1] 11325
> max(x)
[1] 100
```
##### Practice 2
```
> # create a variable
> x = c(1,8,2,6,3,8,5,5,5,5)
> # computing the following
> # (x1+x2+...+x10)/10
> sum(x)
[1] 48
> sum(x)/10
[1] 4.8
> # find the log10(xi) for each i
> log10(x)
 [1] 0.0000000 0.9030900 0.3010300 0.7781513 0.4771213
 [6] 0.9030900 0.6989700 0.6989700 0.6989700 0.6989700
> (x-1.5)/2.5
 [1] -0.2  2.6  0.2  1.8  0.6  2.6  1.4  1.4  1.4  1.4
> max(x) - min(x)
[1] 7
> range(x)
[1] 1 8
```
##### Practice 3
```
# function: diff()
# case: mileages
> diff(mileage)
[1] 313 284 311 280 322 324 302
> mean(mileage)
[1] 66371.75
> max(diff(mileage))
[1] 324
> mean(diff(mileage))
[1] 305.1429
> min(diff(mileage))
[1] 280
> help("diff")
# Lagged Differences
# Returns suitably lagged and iterated differences.
```
##### Practice 4
```
> # case: cell phone bill
> bill = c(46, 33, 39, 37, 46, 30, 48, 32, 49, 35, 30, 48)
> sum(bill)
[1] 473
> min(bill)
[1] 30
> max(bill)
[1] 49
> sum(bill>40)
[1] 5
> (sum(bill>40)/12)*100
[1] 41.66667
```
---
#### Matrix
A matrix can be cosidered as an extension of the vector structure with additional dimensional attributes(rows and columns). A matrix is a collection of vectors of a single type.
```
> # Matrix Operations 01
> matrix(ncol=3,nrow=3)
     [,1] [,2] [,3]
[1,]   NA   NA   NA
[2,]   NA   NA   NA
[3,]   NA   NA   NA
> matrix(1:8,ncol=2)
     [,1] [,2]
[1,]    1    5
[2,]    2    6
[3,]    3    7
[4,]    4    8
> matrix(1:8,ncol=2,byrow=TRUE)
     [,1] [,2]
[1,]    1    2
[2,]    3    4
[3,]    5    6
[4,]    7    8

> x = matrix(1:9,nrow=3)
> x
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9
> dim(x)
[1] 3 3

> y = matrix(1:9, nrow=3, byrow=TRUE)
> y
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
> x==y
      [,1]  [,2]  [,3]
[1,]  TRUE FALSE FALSE
[2,] FALSE  TRUE FALSE
[3,] FALSE FALSE  TRUE
```
**How to get help on R commands?**
```
> ?matrix
# or
> help('matrix')
```
Other matrix operations:
```
> x = matrix(1:9, nrow=3)
> x
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9
> dim(x)
[1] 3 3
> y = matrix(1:9, nrow=3, byrow=TRUE)
> y
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
> dim(y)
[1] 3 3
> x==y
      [,1]  [,2]  [,3]
[1,]  TRUE FALSE FALSE
[2,] FALSE  TRUE FALSE
[3,] FALSE FALSE  TRUE

> x+y
     [,1] [,2] [,3]
[1,]    2    6   10
[2,]    6   10   14
[3,]   10   14   18
> x-y
     [,1] [,2] [,3]
[1,]    0    2    4
[2,]   -2    0    2
[3,]   -4   -2    0
> 2*x + 2*y
     [,1] [,2] [,3]
[1,]    4   12   20
[2,]   12   20   28
[3,]   20   28   36
> # Transpose a matrix
> t(x)
     [,1] [,2] [,3]
[1,]    1    2    3
[2,]    4    5    6
[3,]    7    8    9
> x
     [,1] [,2] [,3]
[1,]    1    4    7
[2,]    2    5    8
[3,]    3    6    9

> # Name the rows and columns of a matrix
> dimnames(x) = list(c("r1", "r2", "r3"), c("c1", "c2", "c3"))
> x = matrix(1:9, nrow=3, dimnames=list(c("r1", "r2", "r3"), c("c1", "c2", "c3")))
> x
   c1 c2 c3
r1  1  4  7
r2  2  5  8
r3  3  6  9
> dimnames(x)
[[1]]
[1] "r1" "r2" "r3"

[[2]]
[1] "c1" "c2" "c3"

> colnames(x)
[1] "c1" "c2" "c3"
> rownames(x)
[1] "r1" "r2" "r3"

> # Add new columns and rows to matrix
> x2 = cbind(x, c(10,11,12))
> dim(x2)
[1] 3 4
> x3 = rbind(x, c(13,14,15))
> dim(x3)
[1] 4 3
> x2
   c1 c2 c3   
r1  1  4  7 10
r2  2  5  8 11
r3  3  6  9 12
> x3
   c1 c2 c3
r1  1  4  7
r2  2  5  8
r3  3  6  9
   13 14 15
```
---
#### Data frame
A data frame can be a collection of vectors of different types. Usually the data is stored in a tabular form, with rows for different person and columns for differenr variables. 
To create a data frame:
```
> height = c(1.75, 1.80, 1.65, 1.90, 1.74, 1.91)
> weight = c(60, 72, 57, 90, 95, 72)
> gender = c('f', 'f', 'f', 'm', 'm', 'm')
> df1 = data.frame(weight, height, gender)
> df1
  weight height gender
1     60   1.75      f
2     72   1.80      f
3     57   1.65      f
4     90   1.90      m
5     95   1.74      m
6     72   1.91      m
> dim(df1)
[1] 6 3
> str(df1)
'data.frame':	6 obs. of  3 variables:
 $ weight: num  60 72 57 90 95 72
 $ height: num  1.75 1.8 1.65 1.9 1.74 1.91
 $ gender: chr  "f" "f" "f" "m" ...

> # Name the rows and columns of a data frame
> rownames(df1) = c("Mike", "Kavya", "Shun", "John", "Dinesh", "Clinton")
> colnames(df1) = c("weight_kgs", "height_meters", "gender_binary")
> df1
        weight_kgs height_meters gender_binary
Mike            60          1.75             f
Kavya           72          1.80             f
Shun            57          1.65             f
John            90          1.90             m
Dinesh          95          1.74             m
Clinton         72          1.91             m

```
---
#### List
A list can be a collection of objects of different types. Each elements of a list is an object and can be any type such as vector, data frame, etc..

To create a list:
```
> # Create a list:
> list1 = list(a=1:5, b=c("Apple", "Pear", "Grape"))
> list1
$a
[1] 1 2 3 4 5

$b
[1] "Apple" "Pear"  "Grape"

> list2 = list(a=rep(2,3), b=1:6, c=c("Cat", "Dog", "Sheep", "Fish"))
> list2
$a
[1] 2 2 2

$b
[1] 1 2 3 4 5 6

$c
[1] "Cat"   "Dog"   "Sheep" "Fish"

> # Access list elements
> list1$"a"
[1] 1 2 3 4 5
> list2[["a"]]
[1] 2 2 2
```
---
### R Packages
```
> install.packages('datasets')
Warning in install.packages :
  package ‘datasets’ is a base package, and should not be updated   # R studio
> library(datasets)

# E.G.: "women" dataset
> data("women")
> str(women)
'data.frame':	15 obs. of  2 variables:
 $ height: num  58 59 60 61 62 63 64 65 66 67 ...
 $ weight: num  115 117 120 123 126 129 132 135 139 142 ...
> # str() function: compactly displaying the internal structure of a R object
> dim(women)
[1] 15  2
> head(women)
  height weight
1     58    115
2     59    117
3     60    120
4     61    123
5     62    126
6     63    129
> head(women, n=10)
   height weight
1      58    115
2      59    117
3      60    120
4      61    123
5      62    126
6      63    129
7      64    132
8      65    135
9      66    139
10     67    142
> tail(women, n=10)
   height weight
6      63    129
7      64    132
8      65    135
9      66    139
10     67    142
11     68    146
12     69    150
13     70    154
14     71    159
15     72    164
> force(women)
   height weight
1      58    115
2      59    117
3      60    120
4      61    123
5      62    126
6      63    129
7      64    132
8      65    135
9      66    139
10     67    142
11     68    146
12     69    150
13     70    154
14     71    159
15     72    164
> table(women$height)

58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 
 1  1  1  1  1  1  1  1  1  1  1  1  1  1  1 
# 1: appear once
> summary((women$weight))
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  115.0   124.5   135.0   136.7   148.0   164.0 
> summary(women$weight)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  115.0   124.5   135.0   136.7   148.0   164.0

> # Calculate the body mass index(BMI)
> women$BMI = (women$weight/women$height**2)*703
> summary(women$BMI)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
  22.09   22.22   22.46   22.72   23.14   24.03 
```
---
### Factor
```
> # Logical checks and for loops
> # Create a new variable: height_group
> # Value "Ht_Grp_gt60" when height > 60
> # Value "Ht_Grp_le60" when height <= 60

> dim(women)
[1] 15  3

> # Option 1
> for (i in (1:15))
+ {
+ if(women$height[i]>60)
+  {
+     women$height_group[i] = "Ht_Grp_gt60"
+  }
+ else if (women$height[i] <= 60)
+  {
+     women$height_group[i] = "Ht_Grp_le60"
+  }
+ }

> women$height_group_factor = factor(women$height_group)
> table(women$height_group_factor)

Ht_Grp_gt60 Ht_Grp_le60 
         12           3
> women
   height weight      BMI height_group height_group_factor
1      58    115 24.03240  Ht_Grp_le60         Ht_Grp_le60
2      59    117 23.62856  Ht_Grp_le60         Ht_Grp_le60
3      60    120 23.43333  Ht_Grp_le60         Ht_Grp_le60
4      61    123 23.23811  Ht_Grp_gt60         Ht_Grp_gt60
5      62    126 23.04318  Ht_Grp_gt60         Ht_Grp_gt60
6      63    129 22.84883  Ht_Grp_gt60         Ht_Grp_gt60
7      64    132 22.65527  Ht_Grp_gt60         Ht_Grp_gt60
8      65    135 22.46272  Ht_Grp_gt60         Ht_Grp_gt60
9      66    139 22.43274  Ht_Grp_gt60         Ht_Grp_gt60
10     67    142 22.23791  Ht_Grp_gt60         Ht_Grp_gt60
11     68    146 22.19680  Ht_Grp_gt60         Ht_Grp_gt60
12     69    150 22.14871  Ht_Grp_gt60         Ht_Grp_gt60
13     70    154 22.09429  Ht_Grp_gt60         Ht_Grp_gt60
14     71    159 22.17358  Ht_Grp_gt60         Ht_Grp_gt60
15     72    164 22.23997  Ht_Grp_gt60         Ht_Grp_gt60
```
Other options:
```
# Option 2:
for (i in (1:15))
{
  if (women[i,1] > 60) 
  {
    women[i,'height_group'] = "Ht_Grp_gt60"
  }
  else if (women[i,1] <= 60) 
  {
    women[i,'height_group'] = "Ht_Grp_le60"
  }
}

# Option 3:
for (i in (1:15))
{
  if (women[i,'height'] > 60) 
  {
    women[i,'height_group'] = "Ht_Grp_gt60"
  }
  else if (women[i,'height'] <= 60) 
  {
    women[i,'height_group'] = "Ht_Grp_le60"
  }
}


```

The character variable height_group can be used to create a new variable height_group_factor with a special data structure called **factor** and with **level**s 'Ht_Grp_le60' and ‘Ht_Grp_gt60'. Factors will come in handy when specific statitical tests are used.

Factors can also be labeled, ordered and recoded.
```
> # Case: dataset ToothGrowth
> data("ToothGrowth")
> dim(ToothGrowth)
[1] 60  3
> head(ToothGrowth)
   len supp dose
1  4.2   VC  0.5
2 11.5   VC  0.5
3  7.3   VC  0.5
4  5.8   VC  0.5
5  6.4   VC  0.5
6 10.0   VC  0.5
> tail(ToothGrowth)
    len supp dose
55 24.8   OJ    2
56 30.9   OJ    2
57 26.4   OJ    2
58 27.3   OJ    2
59 29.4   OJ    2
60 23.0   OJ    2
> # orange juice coded OJ; ascorbic acid coded as VC
```
---
Suppose here are 3 files: <ToothGrowth.txt>, <ToothGrowth.csv>, <ToothGrowth.xlsx>
### Data import and export
1. Import
**TXT file:**
```
> TG_txt = read.table(file="/Users/Pearl/BE7022/Week1_L1/ToothGrowth.txt", header=TRUE)
> summary(TG_txt)
      len            supp                dose      
 Min.   : 4.20   Length:60          Min.   :0.500  
 1st Qu.:13.07   Class :character   1st Qu.:0.500  
 Median :19.25   Mode  :character   Median :1.000  
 Mean   :18.81                      Mean   :1.167  
 3rd Qu.:25.27                      3rd Qu.:2.000  
 Max.   :33.90                      Max.   :2.000
# The summary function can't summary the character variable, let's use the table function:
> table(TG_txt$supp)

OJ VC 
30 30 

> # Convert the character variable supp into a factor so summary function can summarize it
> TG_txt$supp = factor(TG_txt$supp)
> summary(TG_txt)
      len        supp         dose      
 Min.   : 4.20   OJ:30   Min.   :0.500  
 1st Qu.:13.07   VC:30   1st Qu.:0.500  
 Median :19.25           Median :1.000  
 Mean   :18.81           Mean   :1.167  
 3rd Qu.:25.27           3rd Qu.:2.000  
 Max.   :33.90           Max.   :2.000 
```
*Q: What is the difference bwtween the character and the factor?*
> Use character if your data is just strings that do not hold specific meaning; use factor if it's a categorical variable with a limited set of values. The main advantages of using factors are: you get an error if you try to give a new value that is not in the levels (so that can save you from typos)

> In R, a factor is a data type that is used to represent **categorical** data, while a character data type is used to represent text data.

**CSV file:**
```
> TG_csv = read.csv(file="/Users/Pearl/BE7022/Week1_L1/ToothGrowth.csv", header=TRUE)
> dim(TG_csv)
[1] 60  3
> head(TG_csv)
   len supp dose
1  4.2   VC  0.5
2 11.5   VC  0.5
3  7.3   VC  0.5
4  5.8   VC  0.5
5  6.4   VC  0.5
6 10.0   VC  0.5

```
**XLSX file:**
```
> # install.packages("openxlsx")
> library('openxlsx')
> TG_xlsx = read.xlsx("/Users/Pearl/BE7022/Week1_L1/ToothGrowth.xlsx", sheet=1, colNames=TRUE) # This file just has one sheet.
> dim(TG_xlsx)
[1] 60  3
> head(TG_xlsx)
   len supp dose
1  4.2   VC  0.5
2 11.5   VC  0.5
3  7.3   VC  0.5
4  5.8   VC  0.5
5  6.4   VC  0.5
6 10.0   VC  0.5

# Sort
> TG_sort1 = TG_xlsx[order(TG_xlsx$len),]
> TG_sort2 = TG_xlsx[order(-TG_xlsx$len),]
> head(TG_sort1)
   len supp dose
1  4.2   VC  0.5
9  5.2   VC  0.5
4  5.8   VC  0.5
5  6.4   VC  0.5
10 7.0   VC  0.5
3  7.3   VC  0.5
> head(TG_sort2)
    len supp dose
23 33.9   VC    2
26 32.5   VC    2
56 30.9   OJ    2
30 29.5   VC    2
59 29.4   OJ    2
50 27.3   OJ    1
> TG_sort3 = TG_xlsx[order(TG_xlsx$len, TG_xlsx$dose),]
> TG_sort4 = TG_xlsx[order(TG_xlsx$len, -TG_xlsx$dose),]
> head(TG_sort3)
   len supp dose
1  4.2   VC  0.5
9  5.2   VC  0.5
4  5.8   VC  0.5
5  6.4   VC  0.5
10 7.0   VC  0.5
3  7.3   VC  0.5
> head(TG_sort4)
   len supp dose
1  4.2   VC  0.5
9  5.2   VC  0.5
4  5.8   VC  0.5
5  6.4   VC  0.5
10 7.0   VC  0.5
3  7.3   VC  0.5

# Subsets:
> # Create subsets of columns and/or rows
> TG_subset1 = subset(TG_xlsx, select=c(len, dose))
> TG_subset2 = subset(TG_xlsx, select=c(len, dose), subset=(dose>0.5))
> TG_subset3 = subset(TG_xlsx, select=c(len, supp, dose), subset=(dose>0.5 & supp=="OJ"))
> head(TG_subset1)
   len dose
1  4.2  0.5
2 11.5  0.5
3  7.3  0.5
4  5.8  0.5
5  6.4  0.5
6 10.0  0.5
> head(TG_subset2)
    len dose
11 16.5    1
12 16.5    1
13 15.2    1
14 17.3    1
15 22.5    1
16 17.3    1
> head(TG_subset3)
    len supp dose
41 19.7   OJ    1
42 23.3   OJ    1
43 23.6   OJ    1
44 26.4   OJ    1
45 20.0   OJ    1
46 25.2   OJ    1
```
2. Export
```
> head(TG_subset1)
   len dose
1  4.2  0.5
2 11.5  0.5
3  7.3  0.5
4  5.8  0.5
5  6.4  0.5
6 10.0  0.5
> dim(TG_subset1)
[1] 60  2
> str(TG_subset1)
'data.frame':	60 obs. of  2 variables:
 $ len : num  4.2 11.5 7.3 5.8 6.4 10 11.2 11.2 5.2 7 ...
 $ dose: num  0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 0.5 ...
> # A data frame can be export to a .txt file using write.table function.
> write.table(TG_subset1, file="/Users/Pearl/BE7022/Week1_L1/TG_subset1.txt", col.names=TRUE, row.names=FALSE, quote=FALSE)
# row.names=FALSE prevents writing the data frame's row numbers as a column in output .txt file
# quote=FALSE prevents surrounding of any character or factor columns by double quotes
# wirte.csv

> write.xlsx(TG_subset3, file="/Users/Pearl/BE7022/Week1_L1/TG_subset3.xlsx", sheetNames="Sheet1", colNames=TRUE, rowNames=FALSE)
# need pkg 'openxlsx'

```
---
## Lecture 2
Typically, a statistical study proceeds as follows:
1. Have a hypothesis about a phenomenon.
2. Collect data about the phenomenon.
3. Process or analyze the data in order to increase our understanding of the phenomenon under focus.
4. Check whether the data are consistent with the hypothesis.

**Key words:**
- Retrospective study
- Prospective study
  
- Longitudinal study (e.g. Framingham Heart Study)

**Type of statistic**
1. Descriptive Statistics
2. Inferential Statistics
> - population measurements
> - population mean(μ) (the average)
> - Using sample data, guessing or making statements about the parameters of the population is called *Statistical Inference*.
  
**Type of Variables**
1. Categorical variable (or Discrete variable, Qualitatve variable, Nominal variable)
   > with gaps or interruptions
2. Continuous variable (or Quantitive variable; numeric)
   > no gaps or interruption

**Type of Studies**

1. Observational Study
> An observational study collects data as it exists. No intentional interference is allowed.

2. Experimental Study
> An experimental study is one in which the investigator deliberately changes the circumstances of each subject ine the study in order to influence the outcome.
> E.G.: Does taking half of an aspirin tablet three times a week prevents heart attack. 
Conduct an experiment?
> > Conduct an experiment:
> > 1. Identify the target population;
> > 2. Select a sample;
> > 3. Treatment/ Control (randomized, sham/placebo ...)
> > 4. Double-blind studies
> > 5. Follow the for 10 years, say.
> > 6. Collect the revelant data.
*Key words:* Clinical trials, laboratory experimental study, comparative experiment, experimental unit, cross-over experiment

---
**SOME TERMINOLOGY**

Cohort; Prospective study; Retrospective study; Baseline characteristics; Case control study; Matched Case Control Study; Cross-Sectional Study; Placebo; Single-blind study...

> - Baseline Characteristics are values recorded at the time of entry into the study.
> - A Case Control Study is one in which the cases have the disease under focus and controls are a comparative group of not having the disease.
> - A Cross-Sectional Study is one in which information on a variable is collected at one fixed time.



