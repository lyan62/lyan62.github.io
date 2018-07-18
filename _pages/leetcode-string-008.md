---
permalink: /leetcode/string/008
layout: single
classes: wide
title:  "008 String to Integer (atoi)"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---



>  [Original Description](https://leetcode.com/problems/string-to-integer-atoi/description/):
>  converts a string to an integer.
>  First, discards as many whitespace characters as necessary until the first non-whitespace character.
>  The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function
>  If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed. Return 0.

----------------------------
- 要求： 
给一个string,将其转化为*interger*.  
	1. 若string起始为 **空格** ，丢弃 **空格** 直到非空格字符；  
	2. 整数之后的其他字符忽略
	3. 不以 **数字**，**正负号**，或 **空格** 起始的字符，不转换。返回0。
	4. 保留数字的 **正负号**。
	5.  转换后的数字范围应在 $$[−2^{31},  2^{31} − 1]$$, 否则返回边界。
 

--------------------------
- 返回：
string对应的 integer

----------------------------

- 例子：
	- input: "   -42"
	- output: -42
	- input: "words and 987"
	- output: 0

----------------------------
## Solution
- 将string split（去除空格）到list $$l$$, 如果$$l[0]$$ 为数字，判断边界 $$ min((2**31)-1,int(l[0]))$$，返回。  
- 否则， 读取正负号， 之后若第一位非数字，返回0,否则逐位读取string的字符，直到非数字。判断边界。返回值。

```python
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        if len(str)==0:
            return 0
        else:
            l = str.split()
            if l == []:
                return 0
            elif len(l[0]) == 1 and not l[0].isdigit():
                return 0
            elif l[0].isdigit():
                return min((2**31)-1,int(l[0]))
            else:
                out = self.getnumber(l[0])
                return out
    def getnumber(self, str):
        if str[0] == '-':
            sign = -1
            i = 1
        elif str[0] == '+':
            sign = 1
            i = 1
        else: 
            sign = 1
            i = 0
        out = ""
        if not str[i].isdigit():
            return 0
        else:
            while str[i].isdigit():
                out += str[i]
                i += 1
                if i >= len(str):
                    break
            if sign*int(out) <0 :
                return max(-1*(2**31), sign*int(out))
            else:
                return min((2**31)-1, sign*int(out))
```