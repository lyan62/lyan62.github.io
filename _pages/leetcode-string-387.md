---
permalink: /leetcode/string/387
layout: single
classes: wide
title:  "387 First Unique Character in a String"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/first-unique-character-in-a-string/description/):
>  Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.


----------------------------
- 要求： 
给一个string, 找出其中第一个没有重复出现的字母

--------------------------
- 返回：
该字母的index

----------------------------

- 例子：
	- input: "leetcode"
	- output: 0

----------------------------
## Solution
- 遍历string中的字母， 使用dict存储字母的index和出现次数。
- 以index为key排序，如果出现次数==1,则输出该字母。

```python
class Solution(object):
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s == "":
            return -1
        elif len(s) == 1:
            return 0
        else:
            d = {}
            for i in range(len(s)):
                if s[i] not in d:
                    d[s[i]] = [1, i]
                else:
                    d[s[i]][0]+=1
            vlist = list(d.values())
            sorted_list = sorted(vlist, key=lambda x:x[1])
            count = 0
            for x in sorted_list:
                if x[0] ==1:
                    return x[1]
                else:
                    count +=1
                    if count == len(set(s)):
                        return -1
```