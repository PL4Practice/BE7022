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
```
