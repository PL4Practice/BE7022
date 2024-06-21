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
#### Matrix
A matrix can be cosidered as an extension of the vector structure with additional dimensional attributes(rows and columns). A matrix is a collection of vectors of a single type.
```
> # Matrix Operation
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
```
