---
permalink: /leetcode/array/189
layout: single
classes: wide
title:  "189 Rotate array"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


----------------------------------
> [Original Description](https://leetcode.com/problems/rotate-array/description/).
> Given an array, rotate the array to the right by k steps, where k is non-negative.
> Example 1:
    
    Input: [1,2,3,4,5,6,7] and k = 3
    Output: [5,6,7,1,2,3,4]
    Explanation:
    rotate 1 steps to the right: [7,1,2,3,4,5,6]
    rotate 2 steps to the right: [6,7,1,2,3,4,5]
    rotate 3 steps to the right: [5,6,7,1,2,3,4]

> Example 2:

    Input: [-1,-100,3,99] and k = 2
    Output: [3,99,-1,-100]
    Explanation: 
    rotate 1 steps to the right: [99,-1,-100,3]
    rotate 2 steps to the right: [3,99,-1,-100]

----------------------------
- 要求：
给一个数组， 将该数组向右移动 $$k$$ 步。

--------------------------
- 返回：
移动后的数组

----------------------------

- 例子：
	- input:  [1,2,3,4,5,6,7] and k = 3
	- output: [5,6,7,1,2,3,4]
	
----------------------------
## Solution
- Brute-force
逐位移动。 time complexity: $$O(len(nums)*k)$$,  space complexity: $$O(1)$$
```python
class Solution(object):
    def moveonce(self, nums):
        tmp = nums[-1]
        for i in range(len(nums)-1, 0, -1):
            nums[i] = nums[i-1]
        nums[0] = tmp
        return nums
    
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        for i in range(k):
            nums = self.moveonce(nums)
```
-------------------------------------------

- solution 2:  
去掉sol1中的外部循环。 time complexity: $$O(len(nums))$$,
space complexity: $$O(k)$$  

```python
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        k = k % len(nums)
        if k!=0 and len(nums)!= 1:
            tmp = nums[-k:]
            for i in range(len(nums)-1, k-1, -1):
                nums[i] = nums[i-k]
            nums[0:k] = tmp
```

----------------------------------------------
           
- solution 3:     
Time complexity: $$O(n)$$, Auxiliary Space: $$O(1)$$  
With reference to [juggling algorithm](https://www.geeksforgeeks.org/array-rotation/).  

![Juggling algorithm](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/arra.jpg "explanation")
1. 求len(nums)和k的最大公约数: e.x. GCD = 3 if  len(nums) = 12 & k = 3
2. If GCD == 1: 逐位移动（solution 1）
3. else: 将array分为长度为k的chunk
4. 将后面几个chunk的数依次rotate
> e.g. input = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12], k = 3,

	
```python
def leftRotate(nums, k):
    for i in range(gcd(k,len(nums))): # with input = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12], k = 3, gcd=3
        # move i-th values of blocks 
        temp = arr[i]
        j = i
        while 1:
            step = j + k #(go to next chunk)
            if step >= len(nums):
                step = step - len(nums)
            if step == i:
                break
            arr[j] = arr[step]
            j = step
        arr[j] = temp
        
#Fuction to get gcd of a and b
def gcd(a, b):
    if b == 0:
        return a;
    else:
        return gcd(b, a%b)
        
#UTILITY FUNCTIONS
#function to print an array 
def printArray(arr, size):
    for i in range(size):
        print ("%d" % arr[i], end=" ")
# Driver program to test above functions 
arr = [1, 2, 3, 4, 5, 6, 7]
leftRotate(arr, 2, 7)
printArray(arr, 7)
# This code is contributed by Shreyanshi Arun 
```
