---
permalink: /leetcode/ds/
layout: single
classes: wide
title:  "Data Structures"
tags: [leetcode, array]
date:   2018-08-27
sidebar:
  nav: "leetcode"
---

- **Fenwick Tree**
[Fenwick Tree](https://lyan62.github.io/leetcode/array/) 可以用于需要求得截止到index i (inclusive)的所有元素之和， 结构简单易实现。 
	- Main Function: 
		- update()  用于建立fenwick tree
		- sum() 获取前i个元素之和

```python
class FenwickTree(object):
	def __init__(self, n):
		self.n = n
		self.tree = [0] * (n+1)
	
	def lastbit(self, x):
		# return last bit
		return x & -x
	
	def update(self, x):
		# build tree
		while x <= n:
			self.tree[x] += x
			x += self.lastbit(x)
	def sum(self, x):
		# get sum of first x
		res = 0
		while x > 0:
			res += self.tree[x]
			x -= self.lastbit(x)
		return res
```

- **Union Find**
属于图类相关算法
	- Main functions:
		- union() 用于connect两个独立节点, 使存在一条路径可以从 node i 到 node j;
		- find() 用于检查是否两个node connected
	- Related problems:
		- [547 Friend circles](https://leetcode.com/problems/friend-circles/description/)

```python
class UnionFind(object):
	def __init__(self, N):
		self.arr = [i for i in range(N)]  # parent of each node is initialized as itself
		self.n = N
	
	def get_root(self, i):    # if a node is root, it's parent is itself
		while self.arr[i] != i:
			i = self.arr[i]
		return i
	
	def union(self, a, b):
		root_a = self.get_root(a)
		root_b = self.get_root(b)
		
		self.arr[root_a] = root_b   # set parent of a's root to be root_b
	
	def find(self, a, b):
		# if two nodes are connected, they share same root
		if self.get_root(a) == self.get_root(b):
			return True
		else:
			return False
```


The above structure can be improved by building a more balanced tree, where when connecting the two subsets based on the number of elements they already have.
(即， 初始化每个节点size=1, a的size < b的size, 则把root_a的parent设成root_b的parent,同时把root_a的size加到root_b的size上， self.size[root_b] += self.size[root_a]，反向同理)

```python
class WeightedUnion(object):
    # maintaining a binary tree. reduce complexity to O(logN)
    def __init__(self, N):
        self.arr = [i for i in range(N)]
        self.size = [1] * N
        
    def get_root(self, i):
        while self.arr[i] != i:
            i = self.arr[i]
        return i

    def find(self, a, b):
        if self.get_root(a) == self.get_root(b):
            return True
        else:
            return False

    def weighted_union(self, a, b):
        # connect two subsets based on the number of elements in each
        root_a = self.get_root(a)
        root_b = self.get_root(b)

        if self.size[a] < self.size[b]:
            self.arr[root_a] = self.arr[root_b]
            self.size[root_b] += self.size[root_a]
        else:
            self.arr[root_b] = self.arr[root_a]
            self.size[root_a] += self.size[root_b]

```


- **Trie**
树状结构， 可以用dict实现，主要用于search (prefix) string 是否存在。
	- Main Functions
		- add() used to build the tree structure with string saved in path from root to leave
		- search() used to search if a **complete string** exists
		- startswith() used to search if prefix exists
	
```python
class TrieTree(object):
	def __init__(self):
		# implement the tree structure with dictionary
		self.tree = dict()
	
	def add(self, word):
		tree = self.tree
		for char in word:
			if char in tree:
				tree = tree[char]
			else:
				char = dict()
				tree = tree[char]
				
		tree['exist'] = True
	
	def search(self, word):
		# search the complete word
		tree = self.tree
		for char in word:
			if char in tree:
				tree = tree[char]
			else:
				return False
		
		if 'exist' in tree and tree['exist'] == True:
			return True
		else:
			return False
	
	def startswith(self, word):
		# search the prefix
		tree = self.tree
		for char in word:
			if char in tree:
				tree = tree[char]
			else:
				return False
		return True
	tree = TrieTree()

# Testing
tree.add("abc")
tree.add("bcd")
print(tree.tree)
# Print {'a': {'b': {'c': {'exist': True}}}, 'b': {'c': {'d': {'exist': True}}}}
print(tree.startswith("ab")) # True
print(tree.search("ab")) # False
print(tree.search("abc")) # True
print(tree.search("abcd")) # False
```

