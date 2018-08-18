---
title: "683. K Empty Slots"
permalink: /leetcode/array/683
layout: single
classes: wide
tags: [leetcode, array, hard, google]
date:   2018-08-18
sidebar:
  nav: "leetcode"

> [Original Description](https://leetcode.com/problems/k-empty-slots/description/)  
> There is a garden with N slots. In each slot, there is a flower. The N flowers will bloom one by one in N days. In each day, there will be exactly one flower blooming and it will be in the status of blooming since then.

>Given an array flowers consists of number from 1 to N. Each number in the array represents the place where the flower will open in that day.  

>For example, flowers[i] = x means that the unique flower that blooms at day i will be at position x, where i and x will be in the range from 1 to N.  

>Also given an integer k, you need to output in which day there exists two flowers in the status of blooming, and also the number of flowers between them is k and these flowers are not blooming.  

>If there isn't such day, output -1.


----------------------------
- 要求： 
	花园中有N个槽，给定种花的顺序flowers，flowers[i] = x 表示第i天，在第x个槽种下一朵花。  

	给定数字k，求flowers中是否存在某一天，满足相隔k距离的两个端点恰好各有一朵花，而这两朵花之间的k个槽都没有花。


--------------------------
- 返回：  
若有一天符合要求，返回该时间，否则返回-1

----------------------------

- 例子：
	- input:  
	flowers: [1,3,2], k=1
	- output: 2
	(In the second day, the first and the third flower have become blooming.)

----------------------------

## Solution
利用 [Fenwick tree](https://lyan62.github.io/leetcode/array/) ft[k]存储前k个槽一共有多少朵花，则区间[m, n]的花朵总数 = ft[n] - ft[m - 1]

利用该数据结构，遍历flowers即可求解。 

[Reference](http://bookshadow.com/weblog/2017/09/24/leetcode-k-empty-slots/)

```python
class FenwickTree(object):
    def __init__(self, n):
        self.n = n
        self.tree = [0] * (n + 1)
	def lowbit(self, x):
        return x & -x
    def update(self, x, val):  # update value at each index
        while x <= self.n:
            self.tree[x] += val
            x += self.lowbit(x)
    def sum(self, x):         # return sum of first x elements
        res = 0
        while x > 0:
            res += self.tree[x]
            x -= self.lowbit(x)
        return res
class Solution(object):
    def kEmptySlots(self, flowers, k):
        """
        :type flowers: List[int]
        :type k: int
        :rtype: int
        """
        maxn = max(flowers)
        nums = [0] * (maxn + 1)
        ft = FenwickTree(maxn)
        for day_index, position in enumerate(flowers):
            ft.update(position, 1)  # update value
            nums[position] = 1      # this position has a flower open on the day
            if position >= k and ft.sum(position) - ft.sum(position - k - 2) == 2 and nums[position - k - 1]:
                return day_index + 1  # as index starts from 0
            if position + k + 1<= maxn and ft.sum(position + k + 1) - ft.sum(position - 1) == 2 and nums[position + k + 1]:
                return day_index + 1
        return -1
```
Time complexity:$$ O(NlogN)$$ (as sum/update operation in fenwick tree is O(logN)), space complexity: $$O(N)$$. 