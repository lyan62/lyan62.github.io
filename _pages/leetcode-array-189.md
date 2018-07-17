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
[Rotate array](https://leetcode.com/problems/rotate-array/description/).
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



Solutions:
- Brute-force
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
complexity: O(len(nums)*k)
space: O(1)

- solution 2:
remove the outer loop in brute force.
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
complexity: O(len(nums))
space: O(k)
           
- solution 3: [juggling algorithm](https://www.geeksforgeeks.org/array-rotation/)
	1. 求len(nums)和k的最大公约数: e.x. GCD = 3 if  len(nums) = 12 & k =3
	2. if GCD == 1: move using solution 1
	3. else: 将array分为长度为k的chunk
	4. 将后面几个chunk的数依次rotate
	
```python
	#Function to left rotate arr[] of size n by d
	def leftRotate(arr, d, n):
		for i in range(gcd(d,n)):

			# move i-th values of blocks 
			temp = arr[i]
			j = i
			while 1:
				k = j + d
				if k >= n:
					k = k - n
				if k == i:
					break
				arr[j] = arr[k]
				j = k
			arr[j] = temp

	#UTILITY FUNCTIONS
	#function to print an array 
	def printArray(arr, size):
		for i in range(size):
			print ("%d" % arr[i], end=" ")

	#Fuction to get gcd of a and b
	def gcd(a, b):
		if b == 0:
			return a;
		else:
			return gcd(b, a%b)

	# Driver program to test above functions 
	arr = [1, 2, 3, 4, 5, 6, 7]
	leftRotate(arr, 2, 7)
	printArray(arr, 7)

	# This code is contributed by Shreyanshi Arun
```