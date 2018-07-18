---
permalink: /leetcode/string/242
layout: single
classes: wide
title:  "242 Valid anagram"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/valid-anagram/description/):
>  Given two strings s and t , write a function to determine if t is an anagram of s.


----------------------------
- 要求： 
给两个string, s 和 t, 判断t是否是s的anagram(字母组成相同)

--------------------------
- 返回：
True/False

----------------------------

- 例子：
	- input: s = "anagram", t = "nagaram"
	- output: True

----------------------------
## Solution
- 首先判断s和t是否长度相同。
- 用dict记录s中字母及其出现次数。
- 遍历t中字母，从dict中将出现次数减去一次。最后判断dict.values()是否由set(s)长度个0
组成。

```python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        d = {}
        if len(s) == len(t):
            for i in range(len(s)):
                if s[i] not in d:
                    d[s[i]]=1
                else:
                    d[s[i]]+=1
            for i in range(len(t)):
                if t[i] not in d:
                    return False
                else:
                    d[t[i]] -= 1
            if list(d.values()) == [0]*len(set(s)):
                return True
            else:
                return False
        else:
            return False                
```