---
layout: page
title: "Defaultdict, Counter, Sets"
tags: [dicionary, collections, data-structure] 
---

The example cases are trying to count the words in a document:

```python
word_counts = {}
for word in document:
	if word in word_counts:
		word_counts[word] += 1
	else:
		word_counts[word] = 1
```

An other “forgiveness is better than permission” approach and just handle the exception from trying to look up a missing key:

```python
word_counts = {}
for word in document:
	try:
		word_counts[word] += 1
	except KeyError:
		word_counts[word] = 1
```

A third approach is to use get, which behaves gracefully for missing keys: 

```python
word_counts = {} 
for word in document: 
	previous_count = word_counts.get(word, 0)
	word_counts[word] = previous_count + 1
```

## Defaultdict
A defaultdict is like a regular dictionary, except that when you try to look up a key it doesn’t contain, it first adds a value for it using a zero-argument function you provided when you created it.

```python
from collections import defaultdict
word_counts = defaultdict(int) # int() produces 0
for word in document:
	word_counts[word] += 1
```

They can also be useful with list or dict or even your own functions: 

```python
dd_list = defaultdict(list) # list() produces an empty list 
dd_list[2].append(1) # now dd_list contains {2: [1]} 
dd_dict = defaultdict(dict) # dict() produces an empty dict 
dd_dict["Joel"]["City"] = "Seattle" # { "Joel" : { "City" : Seattle"}} 
dd_pair = defaultdict(lambda: [0, 0]) dd_pair[2][1] = 1 # now dd_pair contains {2: [0,1]}
```

## Counter

A Counter turns a sequence of values into a defaultdict(int)-like object mapping keys to counts. We will primarily use it to create histograms:
```python
 from collections import Counter 
 c = Counter([0, 1, 2, 0]) # c is (basically) { 0 : 2, 1 : 1, 2 : 1 } 
```

This gives us a very simple way to solve our word_counts problem: 

```python
word_counts = Counter(document) 
```

A Counter instance has a most_common method that is frequently useful:
```python
# print the 10 most common words and their counts 
for word, count in word_counts.most_common(10): print word, count
```

## Sets

Another data structure is set, which represents a collection of distinct elements:

```python
s = set()
s.add(1) # s is now { 1 }
s.add(2) # s is now { 1, 2 }
s.add(2) # s is still { 1, 2 }
x = len(s) # equals 2
y = 2 in s # equals True
z = 3 in s # equals False
```

*in* is a very fast operation on sets  therefore for a membership test, a set is more
appropriate than a list:

```python
stopwords_list = ["a","an","at"] + hundreds_of_other_words + ["yet", "you"]
"zip" in stopwords_list # False, but have to check every element
stopwords_set = set(stopwords_list)
"zip" in stopwords_set # very fast to check 
```

Also *set* 

A set can be created inside curly braces {} or by using the built-in function set() and ca hold only *distinct* items:

```python
my_set = {1, 2, 3}
item_list = [1, 2, 3, 1, 2, 3]
num_items = len(item_list)	 					# 6
item_set = set(item_list) 							# {1, 2, 3}
num_distinct_items = len(item_set) 		# 3
distinct_item_list = list(item_set) 				# [1, 2, 3]
```


### Sources:
* [Joel Grus - Data Science From Scratch: First Principles with Python](http://joelgrus.com/2015/04/26/data-science-from-scratch-first-principles-with-python/)
* [Stackowerflow - How is membership testing different for a list and a set?](https://stackoverflow.com/questions/5230522/how-is-membership-testing-different-for-a-list-and-a-set) 