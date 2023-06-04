---
title: PYTHON 
date: 2023-05-19 11:27:40 +/-TTTT
categories: [learning, PYTHON]
tags: [learning]     # TAG names should always be lowercase
---

# What is Python?
`Python` is a popular high-level programming language because it is easy to learn, easy to read and write, and flexible for use in a variety of applications. Python was developed in 1991 by Guido van Rossum.

Some of the hallmarks of `Python` include :

* Python uses indents to mark code blocks, making it easy to read and learn.
* Python has many libraries and frameworks that make software development easy, such as NumPy (for numerical computing), Django (for web development), and Pygame (for game development).
* Python is open-source and cross-platform, meaning it can run on various operating systems such as Windows, Linux, and macOS.
* Python supports functional, object, and procedural programming paradigms, so it can be used for a wide variety of applications.

`Python` is usually used to develop desktop applications, web applications, games, data analysis and artificial intelligence. In addition, Python is also the main programming language in the field of data science because of its ability to process and analyze data efficiently.

# Python Syntax

`Hello World !`

if programming is the act of teaching a computer to have a conversation with a user, it would be most useful to first teach the computer how to speak. In Python, this is accompilashed with the `print` statement.

```python
print("thanks for read") 
```

A `print` statement is the easiest way to get your Python program to communicate with you. Being able to command this communication will be one of the most valuable tools in your programming toolbox.

`Execute Python Syntax`

As we learned in the previous page, Python syntax can be executed by writing directly in the Command Line :

```python
>>> print("Hello, World!")
Hello, World!
```

# Python Variables
Variables are containers for storing data values.

`Creating Variables`

Python has no command for declaring a variable.
A variable is created the moment you first assign a value to it.

Example :

```python
x = 1  # type int
y = banz # type string
print(x)
print(y)
```
Variabel tidak perlu dideklarasikan dengan tipe tertentu , dan bahkan dapat mengubah tipe setelah ditetapkan.

`Casting`

If you want to specify the data type of a variable, this can be done with casting.

Example :

```python
x = str(2)    # x will be '2'
y = int(2)    # y will be 2
z = float(2)  # z will be 2.0
```
Get the Type

You can get the data type of a variable with the `type()` function.

Example :

```python
x = 5
y = "Banz"
print(type(x))
print(type(y))
```

Output : 

```
<class 'int'>
<class 'str'>
```

`Variable Names`

A variable can have a short name (like x and y) or a more descriptive name (age, carname, total_volume). 

Rules for Python variables:

* A variable name must start with a letter or the underscore character
* A variable name cannot start with a number
* A variable name can only contain alpha-numeric characters and underscores (A-z, 0-9, and _ )
* Variable names are case-sensitive (age, Age and AGE are three different variables)
* A variable name cannot be any of the Python keywords.

Example :

Legal variable names :

```python
myvar = "BanZ"
my_var = "BanZ"
_my_var = "BanZ"
myVar = "BanZ"
MYVAR = "BanZ"
myvar2 = "BanZ"
```

Illegal variable names :

```python
2myvar = "John"
my-var = "John"
my var = "John"
```

`Python Variables - Assign Multiple Values`

Example :

```python
x, y, z = "blue", "apple", "charry"
print(x)
print(y)
print(z)
```

`Unpack a Collection`

If you have a collection of values in a list, tuple etc. Python allows you to extract the values into variables. This is called unpacking.

Example :

Unpack a list:

```python
fruits = ["apple", "banana", "cherry"]
x, y, z = fruits
print(x)
print(y)
print(z)
```

# Python Data Types

`Built-in Data Types`

In programming, data type is an important concept.

Variables can store data of different types, and different types can do different things.

Python has the following data types built-in by default, in these categories:

* Text Type :	`str`

* Numeric Types :	`int`, `float`, `complex`

* Sequence Types :	`list`, `tuple`, `range`

* Mapping Type :	`dict`

* Set Types :	`set`, `frozenset`

* Boolean Type :	`bool`

* Binary Types :	`bytes`, `bytearray`, `memoryview`

* None Type :	`NoneType`

`Setting the Data Type`

In Python, the data type is set when you assign a value to a variable :

| Example                       | Data Type    |
|-------------------------------|--------------|
| x = "Hello World"             | `str `         |
| x = 20                        | `int `         |
| x = 20.5                      | `float`        |
| x = 1j                        | `complex`      |
| x = ["apple", "banana", "cherry"]   | `list `  |
| x = ("apple", "banana", "cherry")   | `tuple`  |
| x = range(6)                  | `range`        |
| x = {"name" : "John", "age" : 36}   | `dict`  |
| x = {"apple", "banana", "cherry"}   | `set`   |
| x = frozenset({"apple", "banana", "cherry"}) | `frozenset` |
| x = True                      | `bool`         |
| x = b"Hello"                  | `bytes `       |
| x = bytearray(5)              | `bytearray`   |
| x = memoryview(bytes(5))      | `memoryview`  |
| x = None                      | `NoneType`     |

# Python Numbers

There are three numeric types in Python :

* int

* float

* complex

`Int`

Int, or integer, is a whole number, positive or negative, without decimals, of unlimited length.

Example Integers :

```python
x = 1

y = 35656222554887711

z = -3255522

print(type(x))
print(type(y))
print(type(z))
```

`Float`

Float, or "floating point number" is a number, positive or negative, containing one or more decimals.

Example
Floats:

```python
x = 1.10
y = 1.0
z = -35.59

print(type(x))
print(type(y))
print(type(z))
```

`Complex`

Complex numbers are written with a "j" as the imaginary part :

Example
Complex:

```python
x = 3+5j
y = 5j
z = -5j

print(type(x))
print(type(y))
print(type(z))
```

`Type Conversion`

You can convert from one type to another with the `int()`, `float()`, and complex() methods:

Example
Convert from one type to another:

```python
x = 1    # int
y = 2.8  # float
z = 1j   # complex

#convert from int to float:
a = float(x)

#convert from float to int:
b = int(y)

#convert from int to complex:
c = complex(x)

print(a)
print(b)
print(c)

print(type(a))
print(type(b))
print(type(c))
```

# Python Booleans
Booleans represent one of two values : `True` or `False`.

In programming you often need to know if an expression is `True` or `False`.

You can evaluate any expression in Python, and get one of two answers, True or False.

When you compare two values, the expression is evaluated and Python returns the Boolean answer.

Example :

```python
print(10 > 9)
print(10 == 9)
print(10 < 9)
```

When you run a condition in an if statement, Python returns True or False :

Example
Print a message based on whether the condition is True or False:

```python
a = 200
b = 33

if b > a:
  print("b is greater than a")
else:
  print("b is not greater than a")
```

# Python Operators
Operators are used to perform operations on variables and values.

In the example below, we use the `+` operator to add together two values :

```python
print(10 + 5)
```

`Python Arithmetic Operators `

Arithmetic operators are used with numeric values to perform common mathematical operations:

| Operator  | Name            | Example    |
|-----------|-----------------|------------|
| +         | Addition        | x + y      |
| -         | Subtraction     | x - y      |
| *         | Multiplication  | x * y      |
| /         | Division        | x / y      |
| %         | Modulus         | x % y      |
| **        | Exponentiation  | x ** y     |
| //        | Floor division  | x // y     |

`Python Assignment Operators`

Assignment operators are used to assign values to variables :

| Operator | Example | Same As    |
|----------|---------|------------|
| =        | x = 5   | x = 5      |
| +=       | x += 3  | x = x + 3  |
| -=       | x -= 3  | x = x - 3  |
| *=       | x *= 3  | x = x * 3  |
| /=       | x /= 3  | x = x / 3  |
| %=       | x %= 3  | x = x % 3  |
| //=      | x //= 3 | x = x // 3 |
| **=      | x **= 3 | x = x ** 3 |
| &=       | x &= 3  | x = x & 3  |
| |=       | x |= 3  | x = x | 3  |
| ^=       | x ^= 3  | x = x ^ 3  |
| >>=      | x >>= 3 | x = x >> 3 |
| <<=      | x <<= 3 | x = x << 3 |

`Python Comparison Operators`

Comparison operators are used to compare two values:

| Operator | Name                        | Example  |
|----------|-----------------------------|----------|
| ==       | Equal                       | x == y   |
| !=       | Not equal                   | x != y   |
| >        | Greater than                | x > y    |
| <        | Less than                   | x < y    |
| >=       | Greater than or equal to    | x >= y   |
| <=       | Less than or equal to       | x <= y   |

`Python Bitwise Operators`

Bitwise operators are used to compare (binary) numbers :

| Operator | Name             | Description                                                         | Example   |
|----------|------------------|---------------------------------------------------------------------|-----------|
| &        | AND              | Sets each bit to 1 if both bits are 1                                | x & y     |
| \|       | OR               | Sets each bit to 1 if one of two bits is 1                           | x \| y    |
| ^        | XOR              | Sets each bit to 1 if only one of two bits is 1                      | x ^ y     |
| ~        | NOT              | Inverts all the bits                                                | ~x        |
| <<       | Zero fill left shift  | Shift left by pushing zeros in from the right and let the leftmost bits fall off   | x << 2    |
| >>       | Signed right shift   | Shift right by pushing copies of the leftmost bit in from the left, and let the rightmost bits fall off   | x >> 2    |

that's all, maybe later I will update about learning basic python. thanks for reading.