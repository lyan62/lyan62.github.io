---
permalink: /leetcode/string/007
layout: single
classes: wide
title:  "007 Reverse integer"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/reverse-integer/description/):
>  Given a 32-bit signed integer, reverse digits of an integer.


----------------------------
- 要求： 
给一个整数（32bit），将这个数reverse(i.e.从右往左读)，正负不变。
	-  Note: 输入输出数的范围是 $$[−2^{31},  2^{31} − 1]$$

--------------------------
- 返回：
reverse后的数字

----------------------------

- 例子：
	- input: -123
	- output: -321

----------------------------
## Solution
和 [Reverse string](https://lyan62.github.io/leetcode/string/344)采取相同的方法，将数字读入list以后，以中间点为pivot交换两边数字。 同时需要判断数字范围和符号。感觉写的好像有点罗嗦了，回头看看能不能简化。

```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        if x < 0:
            sign = -1
            sl = [s for s in str(x)[1:]]
        else:
            sign = 1
            sl = [s for s in str(x)]
            
        for i in range(len(sl)//2):     # swap numbers aroung pivot
            tmp = sl[i]
            sl[i] = sl[-(i+1)]
            sl[-(i+1)] = tmp
        
        out = sign*int("".join(sl))
		
        if out <= 2**31 -1 and out >= -1*(2**31): # check range
            return out
        else:
            return 0
```