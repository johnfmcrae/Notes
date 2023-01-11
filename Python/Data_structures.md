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

Tuples are another data type which belong to the *Sequence* category, along with *Lists* and *Ranges*. Tuples are similar to lists, however unlike lists they are *immutable*. A tuple is constructed with commas and are displayed within parentheses,

```py
>>> t = 1234, 2222, 'abc'
>>> t
(1234, 2222, 'abc')
```

You can also construct tuples using parentheses. Python also allows for some conveniences such as nesting,

```py
>>> a = (1, 4, 7)
>>> b = a, (5, 3)
>>> b
(1, 4, 7, 5, 3)
```

Finally, empty and single element tuples are defined as follows,

```py
>>> empty = ()
>>> singleton = 'val', # <- note the comma
```

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

A *dictionary* is the Python term for an [associative array](https://en.wikipedia.org/wiki/Associative_array), which is also known as a *map* in other languages. Dictionaries access values by assigning them a unique *key*. Keys can be any immutable type, such as a string or a number. Dictionaries are initialized using a comma-separated list of key-value pairs within curly braces,

```py
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel
{'jack': 4098, 'sape': 413}
```

Entries can be added to the dictionary using a list-like notation. Similarly, ou can access individual values by entering its key as you would when indexing a list,

```py
>>> tel['guido'] = 4127
>>> tel
{'jack': 4098, 'sape': 4139, 'guido': 4127}
>>> tel['jack']
4098
```

Dictionaries also have the handy **`in`** operator which will return a boolean indicating whether or not a key is in a given dictionary.

[Contents](_main_Python_notes.md)
