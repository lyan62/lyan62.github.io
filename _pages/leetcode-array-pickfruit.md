---
title: "I1 Maximum Fruit"
permalink: /leetcode/array/maximumfruit
layout: single
classes: wide
tags: [leetcode, array, google]
date:   2018-08-18
sidebar:
  nav: "leetcode"
---


Ok let me recall this problem, Alice went to a farm for fruit picking, and she got two basket. Each tree is able to produce a single type of fruit and the trees are given in an array. Alice can start from any of the trees and then continue picking to the right. She wanted to pick same kind of fruit in each of the basket so she would stop either when she got the third type of fruit or reached the end of the trees. Given array A = [] of length n, return the maximum number of fruits that Alice can pick. Alice won't throw any fruits she has picked.

---------------------------
- 要求：  
给一个数组，求Alice可以摘到的最多水果数量。
Time complexity $$O(N)$$, space complexity $$O(N)$$


--------------------------
- 返回：
max amount of fruit.

----------------------------

- 例子：
	- input: A = [1,2,1,2,1]
	- output: 5
	
----------------------------

## Solution
设置一个list当作basket, 记录[A[i-1], A[i]]的水果类型，遍历数组，如果水果在已有类型中，counter + 1, alice 终止采摘当前两类水果，进而考虑上一步所采摘的水果和当前水果品种，更新basket， 重复之前步骤。设置max_num变量，如果counter 大于max，更新max.

同时需要注意如果重复出现同一水果类型，则更新basket时需要从A[i-1]第一次出现的时候计数，设置same变量记录重复数，在更新basket时同步更新counter以提高效率。

```python
def solution(A):
    # write your code in Python 3.6
    if len(list(set(A)))<=2:
        return len(A)
    else:
        basket = []
        max_num = 0
        cnt = 0
        same = 1
        for i in range(len(A)):
            if A[i] in basket:
                cnt +=1
                if A[i] == A[i-1]:
                    same += 1
                else:
                    same = 1
            else:
                if len(basket)<2:
                    basket.append(A[i])
                    cnt +=1
                    same=1
                else:
                    basket = [A[i-1], A[i]]
                    cnt=same+1
                    same = 1
            if cnt > max_num:
                max_num = cnt
        return max_num
B = [3,4,3,6,6,7]
print(solution(B))
```



