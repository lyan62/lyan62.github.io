---
permalink: /leetcode/array/009
layout: single
classes: wide
title:  "009 Palindrome Number"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/palindrome-number/description/):
> Determine whether an integer is a palindrome. An integer is a palindrome when it reads the same backward as forward.

----------------------------
- 要求：  
判断所给整数是否是回文。  
	- 能否不转化成string做出


--------------------------
- 返回：
True/False

----------------------------

- 例子：
	- input: 121
	- output: True
	
----------------------------

## Solution
利用math.log()将整数逐位表示，再反向读取，判断反向后的数是否和原数相等。

```python
class Solution:
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        
        ## didn't use string
        import math
        if x<0:
            return False
        elif x>=0  and x<=9:
            return True
        else:
            num_digits  = math.ceil(math.log(x, 10))
            digits = [(x//(10**i))%10 for i in range(num_digits-1, -1, -1)]
			
			# read integer backwards
            r = 0
            for i in range(len(digits)):
                r += digits[-(i+1)]*(10**(num_digits-i-1))  
            if r == x:
                return True
            else:
                return False
```



