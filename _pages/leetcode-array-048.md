---
permalink: /leetcode/array/048
layout: single
classes: wide
title:  "048 Rotate image"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/rotate-image/description/):
>  You are given an n x n 2D matrix representing an image.
>  Rotate the image by 90 degrees (clockwise).
Note: You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

----------------------------
- 要求： 
给一个 N X N 的矩阵，顺时针旋转90度

--------------------------
- 返回：
旋转后的 NXN 矩阵

----------------------------

- 例子：
	- input: 
 [[1,2,3],
  [4,5,6],
  [7,8,9]],
	- output:  
[[7,4,1],
  [8,5,2],
  [9,6,3]]

----------------------------
## Solution
-  i为当前行，j为当前列。
-  一个元素的替换： 
	1. 先将 $$m[i][j]$$放入stack, i.e. stack[0] = $$m[i][j]$$
	2. 原本在 $$m[i][j]$$ 位置的数字会跑到$$m[j][N-1-i]$$ 的位置上去。所以将$$m[j][N-1-i]$$位置的元素也压入stack。
	3. 将$$m[j][N-1-i]$$ 用 stack[0]替换，stack pop。 
	4. 更新当前的行,列位置为j,N-1-i.  
- inner loop: 由于矩阵有四条边，所以需要进行上述替换4次。
- outer loop: 对第i行， 我们只需要从元素$$m[i][i]$$（对角线上的元素） 开始替换，到$$m[i][N-1-i]$$ 结束（从最外圈向最内圈）。
- 
```python
class Solution(object):
    def rotate(self, m):
        """
        :type matrix: List[List[int]]
        :rtype: void Do not return anything, modify matrix in-place instead.
        """
        
        d = len(m)
        def update(m, i,j, tmp): 
            tmp.append(m[j][d-1-i])
            m[j][d-1-i] = tmp[0]
            ip = j
            jp = d-1-i
            tmp.pop(0)
            return m, ip, jp, tmp

        for i in range(d//2):
            for j in range(i,d-1-i):
                tmp = [m[i][j]]
                count = 0
                # need 4 times to update on each side of the matrix
                while count < 4:
                    m,i,j, tmp = update(m,i,j,tmp)
                    count += 1
```