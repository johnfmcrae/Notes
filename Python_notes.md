# Python Notes

These are my collection of notes for the Python programming language. I am still fairly new to Python, so the notes start from the basics. However, since I know C, C++ and MATLAB, I'm going in with an understanding of the principles of programming, including object-oriented programming.

## Installations, Set Up and Python in the Terminal

### Interactive Mode

To enter **interactive mode** from the command line, simply use the command `python3` or `python3.x` where *x* is your current version of Python.

To view all variables, use `dir()`

To delete a variable, use `del <variable>`

To get a newline use `\`

To quit interactive mode, use `quit()`

### pip package installer

To install from pip in the terminal, use

```sh
python3 -m pip install "SomeProject"
```

Note the first two commands, `python3 -m` as many installation instructions simply say `pip install "SomeProject"`

## Python Basics

This document summarizes some of the basic rules and syntax of Python. It roughly covers sections 1 through 4.7 of [the Python Tutorial](https://docs.python.org/3/tutorial/index.html)

### Variables

For more detail, see [the Python Tutorial](https://docs.python.org/3/tutorial/introduction.html#lists)

In Python, you do not define variable types as in C. Python acts more like MATLAB, meaning you can define a number, a string, or a list as in the following examples,

```py
# scalar
x = 2

# string
s = "hello"

# list
a = [1, 2, 3]
```

A couple other notes from the above code:

1. Comments are signaled with the `#` character
2. Lines are ended with a newline character; no semi-colons required

#### Numbers

In Python, you do not define the type of number as you would in other languages such as C. However, Python does differentiate between integers and floats. For example,

```python
a = 3   # a is an int
b = 3.0 # b is a float
```

The `/` operator performs floating point division. If you want integer division, use the `//` operator.

You can also perform casting, for example `print(float(3))` prints `3.0`.

#### Strings

Python strings are a sequence of characters. You can define a string with single quotes `'...'`, double quotes `"..."`, or triple quotes, either `'''...'''` or `"""..."""`. Triple quotes allow you to define multi-line strings.

If you need to use the `'` or `"` character in a string, use `\`, for example `can\'t`

Python does not have a character data type. Instead, characters are simply single element strings.

Strings can be concatenated in Python using the `+` operator. Moreover, two or more *string literals* which are next to each other are automatically concatenated, so `>>> 'Py' 'thon'` becomes `'Python'`.

You can also access the characters in a string using array indices. Indices in Python work in both forward and reverse directions. Therefore,

```py
>>> word = 'Python'
>>> word[0]
'P'
>>> word[-1]
'n'
```

You can also **slice** strings in Python. Slicing means taking a specified chunk, or *slice*, of a string, similar to how you would do so in MATLAB.

```py
>>> word = 'Python'
>>> word[0:2]  # characters from position 0 (included) to 2 (excluded)
'Py'
>>> word[2:5]  # characters from position 2 (included) to 5 (excluded)
'tho'
>>> word[:2]   # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]   # characters from position 4 (included) to the end
'on'
>>> word[-2:]  # characters from the second-last (included) to the end
'on'
```

A useful diagram to visualize slicing and indices:

```no-lang
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```

#### Lists

A **list** in Python is a compound data type specified using square brackets and comma-separated inputs.

```py
sequence = [1, 2, 3, 4, 5] # list of numbers from 1 to 5
empty    = []              # an empty list
```

Lists are indexed from `[0]` and can also be accessed in reverse order, just like the strings above.

Lists are **mutable**. You can change elements directly with the `[n]` notation, or you can **append**, **insert**, or **concatenate** lists.

```py
[1, 2, 2].append(4)   # [1, 2, 2, 4]
[1, 2, 4].insert(2,2) # [1, 2, 2, 4]
[1, 2, 2] + [4]       # [1, 2, 2, 4]
```

### Boolean Operators

#### Comparative operators

Like C

- `==`
- `!=`
- `<`
- `>`
- `<=`
- `>=`

#### Logical Operators

Keywords:

- `and` or `&`
- `or`  or `|`
- `not`

### Control Flow

Python uses indentation for control flow. If you need some blank space, you can use the `pass` statement, for example,

```py
while True:
    pass # satisfies indent
a = 1    # some more valid code
```

#### Loops

Loops are signaled by the `:` operator. To generate the first 10 Fibonacci numbers, for example,

```py
a, b = 0, 1
while a < 10:
    a, b = b, a+b
```

The contents of the loop are determined by the indentation.

For loops in Python are always iterated over a sequence, either a string or a list. For example, a for loop which prints some string lengths would be written as follows,

```py
words = ['cat', 'window',  'be']
for w in words:
    print(w, len(w))
# output:
# cat 3
# window 6
# be 2
```

#### Conditionals

Similar to loops, conditionals are signaled with `:` and indentation. In Python there is **`if`**, **`elif`** and **`else`**.

#### The `break` and `continue` Keywords

The `break` keyword works like that of C, when used it will exit the current `for` or `while` loop.

Python also allows you to use an `else` clause in a `for` or `while` loop. If used, the `else` section will not be run if a `break` is called but will be after a `for` loop's conditions are done or after a `while` loop's condition becomes false.

The `continue` statement, which exists also in C, continues the loop at the next iteration. For example,

```py
for num in range(2, 10):
    if num % 2 == 0:
        print("Found an even number", num)
        continue
    print("Found an odd number", num)
```

### Basic Input and Output

To print to the console, use the `print()` function

#### Formatted String Literals

You can add a variable to a print function like you would in C with `printf("a = %d", a)` as follows,

```py
print(f'a = {a}')
```

### The with Statement

Briefly, **`with`** deals with some exception handling and what is known as **context management** in a more concise way. An example from [the Pyhton docs](https://docs.python.org/3/reference/compound_stmts.html#with),

The following code:

```py
with EXPRESSION as TARGET:
    SUITE
```

is semantically equivalent to:

```py
manager = (EXPRESSION)
enter = type(manager).__enter__
exit = type(manager).__exit__
value = enter(manager)
hit_except = False

try:
    TARGET = value
    SUITE
except:
    hit_except = True
    if not exit(manager, *sys.exc_info()):
        raise
finally:
    if not hit_except:
        exit(manager, None, None, None)
```

## Reading and Writing Python Files

To access a file, use the `open()` funciton,

```py
f = open('workfile', 'w')
```

Files can be opened in different modes, which are,

- `'w'` write
- `'r'` read
- `'a'` append
- `'r+'` reading and writing

By default, a file opened without the mode specifier is set to `'r'`. Adding `'b'` to the mode specifier, for example as `'rb+'`, sets the file stream to binary mode.

The explicit way of file handling is similar to that of C. For example, you could print some text from a file like so,

```py
file = open('welcome.txt')
data = file.read()
print data
file.close()
```

However, the recommended way of handling file I/O is by using the **`with`** statement,

```py
with open('welome.txt.') as file:
    data = file.read()
    print data
# file closed by with statement exit context manager
```

For more info on the **`with`** statement, see [Python Basics](Python%20Basics.md).

It is important to *either* use a **`with`** statement or use `f.close()` on a file so that it is properly freed up after use.

### Methods of File Objects

Once a file, `f` is opened it can be used to,

- read using `f.read(size)`, where `size` is an optional numeric arguments either in characters in normal mode or in bytes if in binary mode
- read a single line with `f.readline()`
- write using `f.write(string)`, which will return the number of characters written

## Appendix: Useful Functions in Python

For the full list of Python's built in functions, see [the documentation](https://docs.python.org/3/library/functions.html)

---

```py
str.join(iterable)
```

Concatenates the elements in `iterable` into a single string. Example,

```py
>>> a = ['ham','eggs']
>>> s = ''.join(a)
hameggs
```

---

```py
len(s)
```

Return the length of a list or a string

---

```py
range(stop)
range(start, stop)
range(start, stop, step)
```

Range returns an immutable sequence of numbers with the given inputs. Strictly speaking, it is not a function.
