---
permalink: /leetcode/array/283
layout: single
classes: wide
title:  "283 Move zeros"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---

---------------------------------------------
>  [Original Description](https://leetcode.com/problems/move-zeroes/description/):
>  Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.  
>  Note: You must do this **in-place** without making a copy of the array.
Minimize the total number of operations.
----------------------------

- 要求：
给一个数组, 把其中所有的0放到其他非0数的后面

--------------------------
- 返回：
整理过的数组

----------------------------

- 例子：
	- input:  [0,1,0,3,12]
	- output: [1,3,12,0,0]

----------------------------
## Solution  
如果当前第i个数是0,则将后面的数左移一位，在末尾加上0, i.e. nums[i:] = nums[i+1:]+[0]  
总共进行数组长度个这样的判断后停止。（否则由于放回末尾的0会死循环）

```python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        i = 0
        count = 0
        l = len(nums)
        
        # handel corner cases
        if l == 2:
            if nums[0] == 0:
                nums[0] = nums[1]
                nums[1] = 0
        elif l>2:             
            while i < l-1:
                # prevent infinite loop
                if count == len(nums):
                    break
                if nums[i] == 0:
                    nums[i:] = nums[i+1:]+[0]
                    count+=1
                else:
                    i+=1
```
------------------------------------------
[Geeksforgeeks的解答](https://www.geeksforgeeks.org/move-zeroes-end-array)： 
1. 用count记录非零数个数，如果当前第i个数非0, 则设第count个非零数为当前数值。
2. 补足0使得count的值等于数组长度。
```python
# better solution: 
# https://www.geeksforgeeks.org/move-zeroes-end-array/
def pushZerosToEnd(arr, n):
    count = 0 
    for i in range(n):
        if arr[i] != 0:
            arr[count] = arr[i]
            count+=1
    while count < n:
        arr[count] = 0
        count += 1
```