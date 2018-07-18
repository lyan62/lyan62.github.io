---
permalink: /leetcode/string/028
layout: single
classes: wide
title: "028 Implement strStr()"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/implement-strstr/description/):
>  Implement strStr(). Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

----------------------------
- 要求： 
给一个string **haystack**,和第二个string **needle**:找出needle 在haystack中第一次出现的index.
	- 如果needle为空，返回0

--------------------------
- 返回：
index

----------------------------

- 例子：
	- input:  haystack = "hello", needle = "ll"
	- output: 2

----------------------------
## Solution
- 有点粗暴的解法：直接用in 判断是否存在。
- 若存在，从haystack 第i个字母开始，看长度为len(needle)的字符们和needle是否匹配。

```python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        
        if needle not in haystack:
            return -1
        elif needle == haystack:
            return 0
        else:
            for i in range(len(haystack)):
                if haystack[i:i+len(needle)] == needle:
                    return i
```