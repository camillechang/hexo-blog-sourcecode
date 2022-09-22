---
title: python3.md
date: 2022-09-10 21:02:22
tags: [Python]
categories: Python
---
#### Basic built-in collection data types in Python:
1. List, ordered and mutable. Allows duplicate members.

- `#Lists allow different data types`

`lista = [5, True, "apple"]`

`print(lista)`
- Some useful methods
reverse(), len(),pop(),remove(), sort(),sorted()

 `#create list with repeated elements
list_with_zeros = [0] * 5
print(list_with_zeros)`

2. Tuple, ordered and immutable. Allows duplicate members.

3. Set, unordered and unindexed. No duplicate members.
- union(),combine elements from both sets, no duplication
- intersection(): take elements that are in both sets
- setA.difference(setB), returns a set with all the elements from the setA that are not in setB.
- setA.symmetric_difference(setB), returns a set with all the elements that are in setA and setB but not in both
- update(),
- difference_update() : Update the set by removing elements found in another set.
- Frozen set, an immutable version of normal set

4. Dictionary, unordered, mutable and indexed. No duplicate members. a collection of key-value pairs

`my_dict = {"name":"Max", "age":28, "city":"New York"}`

`my_dict_2 = dict(name="Lisa", age=27, city="Boston")
`

5. Strings.
- strip(), upper(), lower(), startswitch(), find(), split(),join(), format(),

Link https://www.youtube.com/watch?v=HGOBQPFzWKo&ab_channel=freeCodeCamp.org