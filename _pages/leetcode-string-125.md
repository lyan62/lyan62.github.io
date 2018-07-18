---
permalink: /leetcode/string/125
layout: single
classes: wide
title:  "242 Valid Palindrome"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---

>  [Original Description](https://leetcode.com/problems/valid-palindrome/description/):
>  Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.  
>  Note: For the purpose of this problem, we define empty string as valid palindrome.


----------------------------
- 要求： 
给一个string, 判断是否为回文串。
	- note: 空字符串“”返回True;  只考虑string中的字母数字，忽略大小写以及其他符号。

--------------------------
- 返回：
True/False

----------------------------

- 例子：
	- input: "A man, a plan, a canal: Panama"
	- output: True

----------------------------
## Solution
使用两个指针，一个在头，一个在尾。判断如果当前所指**不是字母或数字**，跳过， 向中间移动指针。如果两指针对应字符一致，向中间移动。直到两指针相遇（while start < end）。如果不一致返回False。

```python
import string
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        start, end = 0, len(s) - 1
        while start < end:
            while start < end and not s[start].isalpha() and not s[start].isdigit():
                start += 1
            while start < end and not s[end].isalpha() and not s[end].isdigit():
                end -= 1
            if start < end and s[start].lower() != s[end].lower():
                return False
            start += 1
            end -= 1
        return True
```