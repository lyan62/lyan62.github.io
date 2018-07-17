---
permalink: /leetcode/array/066
layout: single
classes: wide
title:  "066 Plus one"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/plus-one/description/):
>  Given a non-empty array of digits representing a non-negative integer, plus one to the integer.  The digits are stored such that the most significant digit is at the head of the list, and each element in the array contain a single digit.  You may assume the integer does not contain any leading zero, except the number 0 itself.


----------------------------
- 要求：
给一个数组代表一个interger,给这个interger加1

--------------------------
- 返回：
加1以后的值

----------------------------

- 例子：
	- input:  [1,2,3]
	- output: [1,2,4]
	123+1 = 124 ==> [1,2,4]

----------------------------
## Solution  
逐位相加： 加1后如果和为10，需要处理进位。  
最简单可以转换成int相加再用数组表示，但感觉好像在cheet.
```python
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        
        ### sol1 transfer type
        # out = []
        # i = str(int("".join(str(d)for d in digits))+1)
        # return [int(ii) for ii in i]
        
        ### sol2: add digit by digit
        if digits[-1]+1!= 10:
            return digits[:-1]+ [digits[-1]+1]
        else:
            digits[-1] = 0
            carry = 1
            for i in range(len(digits)-2, -1, -1):
                digits[i]+= carry
                if digits[i] != 10:
                    carry = 0
                    break
                else:
                    digits[i] = 0
                    carry = 1
            if carry == 1:
                digits = [1] + digits
        return digits
```