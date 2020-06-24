---
title: 01_Introduction_Note
tag: py,Python,python
notebook: Python
---

### What is Python?

Python is an interpreted(解释型) high level programming language. It is often classified as a["scripting language"](https://en.wikipedia.org/wiki/Scripting_language) and is considered similar to languages such as Perl, Tcl, or Ruby. The syntax of Python is loosely inspired by elements of C programming.

`python --version`查看版本。

### Why was Python created?

Python is created for the need for a language that would bridge the gap between C and the shell. - Guido van Rossum(Who created Python)

### Getting help

Use the `help()` command to get help on the function or operation and so on.

### Interactive Mode

Python programs always run inside an interpreter.The interpreter is a "console-based" application that normally runs from a command shell.

When you start Python, you get an _interactive_ mode where you can experiment.

If you start typing statements, they will run immediately. There is no edit/compile/run/debug cycle.

```py
>>> print('hello world')
hello world
>>> 37*42
1554
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
>>>
```

This so-called **read-eval-print-loop** (or **REPL**) is very useful for debugging and exploration.

Use the underscore (\_) variable to use the result of the last calculation. _This is only true in the interactive mode._ You never use `_` in a program.

```py
>>>1+2
3
>>>_ + 1
4
```

- `>>>` is the interpreter prompt for starting a new statement.
- `...` is the interpreter prompt for continuing a statement. Enter a blank line to finish typing and run what you've entered.The `...` prompt may or may not be shown depending on your environment.

### Statements

A python program is a sequence of statements:

```python
a = 3 + 4
b = a * 2
print(b)
```

Each statement is terminated by a newline. Statements are executed one after the other until control reaches the end of the file.

### Variables

A variable is a name for a value. You can use letters (lower and
upper-case) from a to z. As well as the character underscore `_`.
Numbers can also be part of the name of a variable, except as the
first character.

### Types

Python is dynamically typed. The perceived "type" of a variable might change as a program executes depending on the current value assigned to it.

### Numbers

Python has 4 types of numbers:

- Booleans
- Integers
- Floating point
- Complex (imaginary numbers)

```py
c = 4 + True # 5
```

*But, don't write code like that. It would be odd.*

```python
a = 37
b = -299392993727716627377128481812241231
c = 0x7fa8      # Hexadecimal
d = 0o253       # Octal
e = 0b10001111  # Binary
```

Common operations:

```a
x + y      Add
x - y      Subtract
x * y      Multiply
x / y      Divide (produces a float)
x // y     Floor Divide (produces an integer)
x % y      Modulo (remainder)
x ** y     Power

bit-wise operators not for float:
x << n     Bit shift left
x >> n     Bit shift right
x & y      Bit-wise AND
x | y      Bit-wise OR
x ^ y      Bit-wise XOR
~x         Bit-wise NOT
abs(x)     Absolute value
```

Floats are represented as double precision using the native CPU representation [IEEE 754](https://en.wikipedia.org/wiki/IEEE_754).
This is the same as the `double` type in the programming language C.

> 17 digits or precision
> Exponent from -308 to 308

Be aware that floating point numbers are inexact when representing decimals.

```python
>>> a = 2.1 + 4.2
>>> a == 6.3
False
>>> a
6.300000000000001
>>>
```

This is **not a Python issue**, but the underlying floating point hardware on the CPU.

use `int()` and `float()` and `bool` to convert.  For example,

```python
>>> int("123")
123
>>> float("1.23")
1.23
>>> bool("False")
True
>>> bool('')
False
>>>
```

### String

Strings are "immutable" or read-only. Once created, the value can't be changed.

```python
>>> s = 'Hello World'
>>> s[1] = 'a'
Traceback (most recent call last):
File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>>
```

**More string methods:**

Strings have a wide variety of other methods for testing and manipulating the text data.
This is a small sample of methods:

```python
s.endswith(suffix)     # Check if string ends with suffix
s.find(t)              # First occurrence of t in s
s.index(t)             # First occurrence of t in s
s.isalpha()            # Check if characters are alphabetic
s.isdigit()            # Check if characters are numeric
s.islower()            # Check if characters are lower-case
s.isupper()            # Check if characters are upper-case
s.join(slist)          # Join a list of strings using s as delimiter
s.lower()              # Convert to lower case
s.replace(old,new)     # Replace text
s.rfind(t)             # Search for t from end of string
s.rindex(t)            # Search for t from end of string
s.split([delim])       # Split string into list of substrings
s.startswith(prefix)   # Check if string starts with prefix
s.strip()              # Strip leading/trailing space

>>>name='   IBM    \n'
>>>name=name.strip()
>>>name
'IBM'
>>>

s.upper()              # Convert to upper case
```

#### Byte Strings

A string of 8-bit bytes, commonly encountered with low-level I/O, is written as follows:

```python
data = b'Hello World\r\n'
```

By putting a little b before the first quotation, you specify that it is a byte string as opposed to a text string.

Indexing is a bit different because it returns byte values as integers.

```python
data[0]   # 72 (ASCII code for 'H')
```

Conversion to/from text strings.

```python
text = data.decode('utf-8') # bytes -> text
data = text.encode('utf-8') # text -> bytes
```

#### Raw Strings

Raw strings are string literals with an uninterpreted backslash. They
are specified by prefixing the initial quote with a lowercase "r".

```python
>>> rs = r'c:\newdata\test' # Raw (uninterpreted backslash)
>>> rs
'c:\\newdata\\test'
```

#### f-Strings

A string with formatted expression substitution.

```python
>>> name = 'IBM'
>>> shares = 100
>>> price = 91.1
>>> a = f'{name:>10s} {shares:10d} {price:10.2f}'
>>> a
'       IBM        100      91.10'
>>> b = f'Cost = ${shares*price:0.2f}'
>>> b
'Cost = $9110.00'
>>>
```

Sometimes you want to create a string and embed the values of
variables into it.

To do that, use an f-string. For example:

```python
>>> name = 'IBM'
>>> shares = 100
>>> price = 91.1
>>> f'{shares} shares of {name} at ${price:0.2f}'
'100 shares of IBM at $91.10'
>>>
```

**Note: This requires Python 3.6 or newer.**  The meaning of the format codes
is covered later.

### Regular Expressions

One limitation of the basic string operations is that they don't
support any kind of advanced pattern matching.  For that, you
need to turn to Python's `re` module and regular expressions.
Regular expression handling is a big topic, but here is a short
example:

```python
>>> text = 'Today is 3/27/2018. Tomorrow is 3/28/2018.'
>>> # Find all occurrences of a date
>>> import re
>>> re.findall(r'\d+/\d+/\d+', text)
['3/27/2018', '3/28/2018']
>>> # Replace all occurrences of a date with replacement text
>>> re.sub(r'(\d+)/(\d+)/(\d+)', r'\3-\1-\2', text)
'Today is 2018-3-27. Tomorrow is 2018-3-28.'
>>>
```

### Commentary

As you start to experiment with the interpreter, you often want to
know more about the operations supported by different objects.  For
example, how do you find out what operations are available on a
string?

Depending on your Python environment, you might be able to see a list
of available methods via tab-completion.  For example, try typing
this:

```python
>>> s = 'hello world'
>>> s.<tab key>
>>>
```

If hitting tab doesn't do anything, you can fall back to the
builtin-in `dir()` function.  `dir()` produces a list of all operations that can appear after the `(.)`.  For example:

```python
>>> s = 'hello'
>>> dir(s)
['__add__', '__class__', '__contains__', ..., 'find', 'format',
'index', 'isalnum', 'isalpha', 'isdigit', 'islower', 'isspace',
'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'partition',
'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit',
'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase',
'title', 'translate', 'upper', 'zfill']
>>>
```
