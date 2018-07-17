---
permalink: /leetcode/array/122
layout: single
classes: wide
title:  "122 Best Time to Buy and Sell Stock II"
tags: [leetcode, array, easy]
date:   2018-07-17
sidebar:
  nav: "leetcode"
---


----------------------------
> [Original description](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/):    
> Say you have an array for which the ith element is the price of a given stock on day i.
> Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).
> Note: You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).

----------------------------
- 要求：
给一个数组，其中第i个元素表示第i天的股票价格。设计算法使得股票买卖获利最大。
	- 可以进行多次买卖
	- 再次购买以前必须卖出持有股

--------------------------
- 返回：
最大收益值

----------------------------

- 例子：
	- input:  [7,1,5,3,6,4]
	- output: 7
	第二天买，第三天卖（5-1 = 4），第四天买，第五天卖（6-3=3）==> 4+3 = 7
	
----------------------------
## Solution
由于可以进行多次买卖，只要输入序列递增，则可以进行利润累加。

```python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        if prices == [] or len(prices) == 1:
            return 0
        else:
            profit = 0
            for i in range(len(prices)-1):
                if prices[i+1] > prices[i]:
                    profit += prices[i+1]-prices[i]
            return profit
        
# with reference to :https://www.cnblogs.com/zuoyuan/p/3765980.html
```
