---
permalink: /leetcode/array/001
layout: single
classes: wide
title:  "036 Validate sudoku"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---

>  [Original Description](https://leetcode.com/problems/valid-sudoku/description/):
>  Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules: 
>  Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the 9 3x3 sub-boxes of the grid must contain the digits 1-9 without repetition.  
![Sudoku](https://upload.wikimedia.org/wikipedia/commons/thumb/f/ff/Sudoku-by-L2G-20050714.svg/250px-Sudoku-by-L2G-20050714.svg.png "Sudoku example")

----------------------------
- 要求：
给一个9x9的数独表，判断是否该表符合规范： 每行/列1-9不重复，每个3x3小格1-9不重复。 


--------------------------
- 返回：
True/False

----------------------------
## Solution
使用了numpy提取列。使用helper function-validaterc 判断是否存在重复。  
使用dict存储数字出现频率，如果当前行/列 当前数字典中已经出现一次则返回false.
先检查行和列，将3x3方格提取成数组，用validaterc判断。

```python
import numpy as np
class Solution(object):
    def isValidSudoku(self, board):
        """
        :type board: List[List[str]]
        :rtype: bool
        """

        # validate row
    
        for row in board:
            if self.validaterc(row) == False:
                return False
        
        # validate col
        board_arr = np.asarray(board)
        for col in range(9):
            if self.validaterc(board_arr[:,col]) == False:
                return False

        # validate square
        for i in range(0,7,3):
            for j in range(0,7,3):
                if self.validatesquare(board, i,j)== False:
                    return False
    
        return True
    
    def validaterc(self, rc):
        flag = True
        d = {"1":0,"2":0,"3":0,"4":0, "5":0, "6":0, "7":0, "8":0,"9":0}
        for r in rc:
            if r != ".":
                if d[r] == 1:
                    flag = False
                    break
                else:
                    d[r]+=1
        return flag
    
    def validatesquare(self, board, i, j):
        square = []
        for r in range(i,i+3):
            square += board[r][j:j+3]
        flag = self.validaterc(square)
        return flag
    
        
```