---
title: "200 Number of Islands"
permalink: /leetcode/tree/200
layout: single
classes: wide
tags: [leetcode, tree, medium]
date:   2018-07-22
sidebar:
  nav: "leetcode"
---


> [Original Description](https://leetcode.com/problems/number-of-islands/description/)  
> Given a 2d grid map of '1's (land) and '0's (water), count the number of islands. An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.


----------------------------
- 要求： 
给一个2D array, 其中 1代表陆地， 0代表海洋，输出该数组所表示的**岛屿**的数量.


--------------------------
- 返回：  
岛屿的数量

----------------------------

- 例子：
	- input:  
	root = [2,1,3], p = 1

  2
 / \
1   3

	- output: 2


----------------------------

## Solution
遍历二维数组，如果当前坐标是陆地，则对陆地进行DFS并标记，标记完所有相邻陆地之后给当前岛屿计数的counter +1。

```python
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        if not grid:
            return 0
        
        count = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                if grid[i][j] == '1':
                    self.dfs(grid, i, j)
                    count += 1
        return count
		
    def dfs(self, grid, i, j):
        if i<0 or j<0 or i>=len(grid) or j>=len(grid[0]) or grid[i][j] != '1':
            return
        grid[i][j] = '#'
        self.dfs(grid, i+1, j)
        self.dfs(grid, i-1, j)
        self.dfs(grid, i, j+1)
        self.dfs(grid, i, j-1)         
```