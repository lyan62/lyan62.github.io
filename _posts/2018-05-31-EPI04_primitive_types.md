---
layout: single
classes: wide
title:  "NOTES: EPI Ch4 Primitive Types"
date:   2018-05-30
---

## Primitive Types

### 4.1 Parity
Parity fo a binary word is 1 if the number of 1s in the word is odd, o.w. is 0.


```python
def parity(x):  # brute force
    result = 0
    while x:
        result ^= x & 1
        x >>= 1
    return result  # O(n)

#------------------------ improve--------------------------#
# Trick: x & (x-1) equals x with its lowest set bit erased.#
# e.g. (00101100) & (00101011) = 00101000
#----------------------------------------------------------#

def parity_good(x):
    resutl = 0
    while x:
        result ^= 1 
        x &= x-1  # drops lowest set bit of x
    return result  # O(k) where k is the number of bits set (= number of 1's in the binary number)
```


```python
## ex
parity(3)
```




    0



### P4_1 count bits
count number of 1s in binary representation of an integer ([img source](https://www.geeksforgeeks.org/wp-content/uploads/setbit.png)).
<img src="setbit.png",alt="setbit">


```python
def count_bits(x):
    num_bits = 0
    while x:
        num_bits += x & 1   # go through digit by digit
        x >>= 1             # right shift 1 digit
    return num_bits         # O(n)
```


```python
def count_bits_recur(x):
    
    # base case
    if (x == 0):
        return 0
 
    else:
        # if last bit set add 1 else
        # add 0
        return (x & 1) + count_bits_recur(x >> 1)  # O(logn)
```


```python
## ex
count_bits(9)
```




    2




```python
## ex
count_bits_recur(4)
```




    1


