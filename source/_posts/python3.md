---
title: Python 3 Collection Data Types
date: 2022-09-10 21:02:22
tags: [Python]
categories: Python
---
## English Version

### Basic Built-in Collection Data Types in Python

1. **List**: ordered and mutable; allows duplicate members.

Lists can contain different data types:

```python
lista = [5, True, "apple"]
print(lista)
```

Useful functions and methods include `reverse()`, `len()`, `pop()`, `remove()`, `sort()`, and `sorted()`.

Create a list containing repeated elements:

```python
list_with_zeros = [0] * 5
print(list_with_zeros)
```

2. **Tuple**: ordered and immutable; allows duplicate members.

3. **Set**: unordered and unindexed; does not allow duplicate members.
   - `union()`: combines elements from both sets without duplication.
   - `intersection()`: returns elements present in both sets.
   - `setA.difference(setB)`: returns elements in `setA` that are not in `setB`.
   - `setA.symmetric_difference(setB)`: returns elements in either `setA` or `setB`, but not both.
   - `update()`: adds elements from another set.
   - `difference_update()`: updates the set by removing elements found in another set.
   - A frozen set is an immutable version of a normal set.

4. **Dictionary**: insertion-ordered in modern Python, mutable, and accessed by key. It stores key-value pairs, and keys cannot be duplicated.

```python
my_dict = {"name":"Max", "age":28, "city":"New York"}
my_dict_2 = dict(name="Lisa", age=27, city="Boston")
```

5. **String**: an immutable sequence of characters.
   - Useful methods include `strip()`, `upper()`, `lower()`, `startswith()`, `find()`, `split()`, `join()`, and `format()`.

Source: https://www.youtube.com/watch?v=HGOBQPFzWKo&ab_channel=freeCodeCamp.org

---

## 中文版

### Python 的基本内置集合数据类型

1. **列表（List）**：有序且可变，允许重复成员。

列表可以包含不同的数据类型：

```python
lista = [5, True, "apple"]
print(lista)
```

常用函数和方法包括 `reverse()`、`len()`、`pop()`、`remove()`、`sort()` 和 `sorted()`。

创建包含重复元素的列表：

```python
list_with_zeros = [0] * 5
print(list_with_zeros)
```

2. **元组（Tuple）**：有序且不可变，允许重复成员。

3. **集合（Set）**：无序且不通过索引访问，不允许重复成员。
   - `union()`：合并两个集合的元素，不保留重复项。
   - `intersection()`：返回两个集合中都存在的元素。
   - `setA.difference(setB)`：返回 `setA` 中存在但 `setB` 中不存在的元素。
   - `setA.symmetric_difference(setB)`：返回只存在于 `setA` 或 `setB` 其中之一、但不同时存在于两者中的元素。
   - `update()`：添加另一个集合中的元素。
   - `difference_update()`：删除另一个集合中也存在的元素，从而更新当前集合。
   - 冻结集合（frozen set）是普通集合的不可变版本。

4. **字典（Dictionary）**：在现代 Python 中保持插入顺序，可变，并通过键访问。字典存储键值对，键不能重复。

```python
my_dict = {"name":"Max", "age":28, "city":"New York"}
my_dict_2 = dict(name="Lisa", age=27, city="Boston")
```

5. **字符串（String）**：不可变的字符序列。
   - 常用方法包括 `strip()`、`upper()`、`lower()`、`startswith()`、`find()`、`split()`、`join()` 和 `format()`。

来源：https://www.youtube.com/watch?v=HGOBQPFzWKo&ab_channel=freeCodeCamp.org
