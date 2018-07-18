---
permalink: /leetcode/string/014
layout: single
classes: wide
title: "014 Longest Common Prefix"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/longest-common-prefix/description/):
>  Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string "".

----------------------------
- 要求：  
给一组string, 求出他们共同的最长的prefix， 如果没有prefix，返回“”。


--------------------------
- 返回：
prefix

----------------------------

- 例子：
	- input: ["flower","flow","flight"]
	- output: "fl"
	
----------------------------

## Solution
-  偷懒的办法是直接使用： os.path.commonprefix(strs)
-  将string们排序，然后用第一个string中的字符与其余string 中的逐个比较，记录共有的string数量，如果所 记录的数量 = string的个数，将该字符累加到输出的字符中。 

```python
class Solution(object):
    class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        # import os
        # return os.path.commonprefix(strs)
        
        if len(strs) == 0: 
			return ""
        if len(strs) == 1: 
			return strs[0]
        sorted_strs = sorted(strs, key=len)
        out = ""
        for i,w in enumerate(sorted_strs[0]):
            cnt = 0
            for str in sorted_strs[1:]:
                if w == str[i]:
                    cnt+=1
                else:
                    return out
                    break
                    
            if cnt == len(strs)-1:
                out+=w
        return out  
```