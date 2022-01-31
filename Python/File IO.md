# Reading and Writing Python Files

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

## Methods of File Objects

Once a file, `f` is opened it can be used to,

- read using `f.read(size)`, where `size` is an optional numeric arguments either in characters in normal mode or in bytes if in binary mode
- read a single line with `f.readline()`
- write using `f.write(string)`, which will return the number of characters written
