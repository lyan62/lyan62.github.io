---
permalink: /leetcode/array/360
layout: single
classes: wide
title:  "350 Intersection of two arrays II"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


>  [Original Description](https://leetcode.com/problems/intersection-of-two-arrays-ii/description/):
>  Given two arrays, write a function to compute their intersection.
----------------------------
- 要求：
给两个数组，找出其重合。

--------------------------
- 返回：
重合部分

----------------------------

- 例子：
	- input:  [1,2,2,1], [2,2]
	- output: [2,2]

----------------------------
## Solution
给两数组排序，然后对两数组逐个元素比较，将重合部分放进结果。

```python
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        
        # check length and sort
        
        if len(nums1) <= len(nums2):
            shorter = sorted(nums1)
            longer = sorted(nums2)
        else:
            shorter = sorted(nums2)
            longer = sorted(nums1)
        
        # use two pointers in each of the array
        s = 0
        l = 0
        out = []
        while s < len(shorter) and l < len(longer):
            if shorter[s] <longer[l]:
                s += 1
            elif shorter[s] >  longer[l]:
                l += 1
            else:
                out.append(shorter[s])
                s+=1
                l+=1
        return out
```