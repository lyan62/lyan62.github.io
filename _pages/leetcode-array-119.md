---
permalink: /leetcode/array/119
layout: single
classes: wide
title:  "119 Pascal's Triangle II"
tags: [leetcode, array, easy]
date:   2018-07-20
sidebar:
  nav: "leetcode"
---

>  [Original Description](https://leetcode.com/problems/pascals-triangle-ii/description/):
> Given a non-negative index k where k ≤ 33, return the kth index row of the Pascal's triangle. Note that the row index starts from 0.  
> ![pascal's triangle](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)


----------------------------
- 要求： 
给一个数 i, 返回pascal三角中对应的第 i+1 行



--------------------------
- 返回：
array

----------------------------

- 例子：
	- input: 3
	- output: [1 3 3 1]
	
----------------------------

## Solution
Recursive地代入行数，保存上一行的输出，利用上一行计算下一行。  
Note:如果没有保存上一步的输出， 会超时

```python
class Solution:
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """
        if rowIndex == 0:
            return [1]
        elif rowIndex == 1:
            return [1, 1]
        else:
            ans = [1]
            last = self.getRow(rowIndex-1)
            for i in range(1, rowIndex//2+1 ,1):
                ans.append(last[i-1]+last[i])
            
            if rowIndex % 2 == 0:
                ans += ans[::-1][1:]
            else:
                ans += ans[::-1]
            return ans
```



