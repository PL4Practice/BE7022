# Week 01
## Lecture 1
**Data structure:**
| Dimension | Homogeneous | Heterogeneous |
|-----------|--------------|------------- |
| one-dimensional | Atomic Vector | List |
| two-dimensional | Matrix | Data Frame |
| multi-dimensional | Array | List |

**Vector**
> logical; integer; double(numeric); character; complex; raw

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
```
