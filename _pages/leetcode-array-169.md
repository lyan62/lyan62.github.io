---
permalink: /leetcode/array/169
layout: single
classes: wide
title:  "16 Major Elements"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/majority-element/description/):
> Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times. You may assume that the array is non-empty and the majority element always exist in the array.


----------------------------
- 要求： 
给一个长度为 n 的数组，找出其中占大多数的元素（即至少出现 n/2次）。




--------------------------
- 返回：
该元素

----------------------------

- 例子：
	- input: [3, 2, 3]
	- output: 3


----------------------------

## Solution
用cnt计数，遍历数组，如果当前元素为candidate, cnt+=1 否则 cnt -=1, 如果cnt == 0, 设置当前元素为candidate。返回candidate。 

（由于我们想要的输出至少存在 n/2次，而只有cnt==0时才更换candidate。所以保留的candidate即为所需元素。）
- time complexity: $$O(n)$$, space $$O(1)$$。
- 另两种解法见 [acwing 169](https://www.acwing.com/solution/leetcode/content/277/)
 
```python
class Solution:
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        cnt = 0
        cand = nums[0]
        for n in nums:
            if cnt == 0:
                cand = n
            
            if n == cand:
                cnt += 1
            else:
                cnt -= 1
                
        return cand
```



