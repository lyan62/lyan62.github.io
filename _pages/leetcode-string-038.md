---
permalink: /leetcode/string/038
layout: single
classes: wide
title: "038 Count and Say"
tags: [leetcode, string, easy]
date:   2018-07-18
sidebar:
  nav: "leetcode"
---



>  [Original Description](https://leetcode.com/problems/count-and-say/description/):
>  The count-and-say sequence is the sequence of integers with the first five terms as following:  
1...     1  
2...     11  
3...     21  
4...     1211  
5...     111221  
1 is read off as "one 1" or 11.  
11 is read off as "two 1s" or 21.  
21 is read off as "one 2, then one 1" or 1211.  
Given an integer n, generate the nth term of the count-and-say sequence.
Note: Each term of the sequence of integers will be represented as a string.

----------------------------
- 要求：  
给一个整数 n 


--------------------------
- 返回：
n 所对应产生的count-and-say 序列。

----------------------------

- 例子：
	- input: 4
	- output: "1211"
	1： 读作1个1,则表示为11  
	11：读作2个1,则表示为21
	21：读作1个2,1个1,则表示为1211
	
----------------------------

## Solution
- 从 ‘1’ 开始作为输入用 cal() 函数迭代。迭代 n 次。
- 每次： 初始化 cnt = 1(记录当期数字有几个)，输出string为空，遍历string s 中的数字。
	-  如果当前数字 c $$\neq$$ 下一个数字，将 cnt + c 累加到输出string上。
	-  否则， 给cnt += 1。继续下一个数字。
	- 注意：下一个数字的坐标不能超过 len(s)

```python
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        s='1'
        for i in range(1,n):
            s=self.cal(s)
        return s
        
    def cal(self,s):          
        cnt=1
        length=len(s)
        ans=''
        for i ,c in enumerate(s):
            if i+1 < length and s[i]!=s[i+1]:
                ans=ans+str(cnt)+c
                cnt=1
            elif i+1 <length:
                cnt=cnt+1
                
        ans=ans+str(cnt)+c    
        return ans
```