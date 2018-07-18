---
permalink: /leetcode/string/344
layout: single
classes: wide
title:  "344 Reverse string"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/reverse-string/description/):
>  Write a function that takes a string as input and returns the string reversed.

----------------------------
- 要求： 
将一个给定string reverse

--------------------------
- 返回：
reverse后的string

----------------------------

- 例子：
	- input: 'hello'
	- output:  'olleh'

----------------------------
## Solution
以string的中间位置为pivot，将其左右两边character进行交换。
Note: 中间位置 = $$len(s)//2$$

```python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        l = [ss for ss in s]
        for i in range(len(l)//2):
            tmp = l[i]
            l[i] = l[-(i+1)]
            l[-(i+1)] = tmp
        return "".join(l)
```