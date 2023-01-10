# Data Structures in Python

In addition to the list data structure, which we have seen in [Python Basics](Python_basics.md), there are also other data structures available in Python which are common to other languages.

## More on Lists

Lists have methods which allow them to be used as stacks or queues. Note the following,

- `list.pop()`
- `list.popleft()`
- `list.dequeue(`*`elements`*`)`
- `list.append(`*`elements`*`)`

It is possible to delete an element in a list at a given value using the **`del`** operator, for example

```py
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
```

Using **`del`** without and index deletes the entire variable.

## Tuples and Sequences

to do

## Sets

Recall that in computer science, a [set](https://en.wikipedia.org/wiki/Set_(abstract_data_type)) is a data type which contains an unordered collection of unique elements. In Python, sets are created using either curly braces `{}` or the `set()` function. Empty sets can *only* be made using `set()`. Some example code from [the docs](https://docs.python.org/3/tutorial/datastructures.html#sets),

```py
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # show that duplicates have been removed
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # fast membership testing
True
>>> 'crabgrass' in basket
False

>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # unique letters in a
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # letters in a but not in b
{'r', 'd', 'b'}
```

## Dictionaries

A *dictionary* is the Python term for an [associative array](https://en.wikipedia.org/wiki/Associative_array), which is also known as a *map* in other languages.
