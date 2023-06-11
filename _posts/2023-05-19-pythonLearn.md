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

# Basic Syntax

Below is an example of a Python function used to print. In Python to print just use the function `print()`, where something to be printed must be placed between the opening and closing brackets, even in Python version 3.x you don't have to use curly braces, just separate them with a space.

If you want to print the String data type directly, you must enclose it in quotes first.

```python
print("Hellow World")
```

When you run the script above, you will see the output in the form of textHello World

# Python Case Sensitivity

Python is case sensitive, this means that uppercase and lowercase letters are different. For example if you use the print function with lower case `print()`it will work. Another thing if you use capital letters `Print()or PRINT()`, an error message will appear.

This rule applies to variable names or other functions.

# Python comments

`Python comments` are lines of text that are ignored by the interpreter during program execution. They are used to provide explanatory or descriptive information about the code to make it more readable and understandable for other programmers or even for yourself when revisiting the code later.

In Python, comments start with the hash `#` symbol and continue until the end of the line. Here's an example:

Below is an example of using comments in Python.

```python
# This is a comment.
# It provides additional information about the code.

print("Hello, World!")  # This line prints a greeting message.
```

# Python Data Types

A data type is a media or memory on a computer that is used to store information.
Python itself has a data type that is quite unique when we compare it to other programming languages.

Following are the data types of the Python programming language :

| Data Type     | Example                  | Explanation                                                |
|---------------|--------------------------|------------------------------------------------------------|
| Booleans      | True or False            | Represents true (with a value of 1) or false (with a value of 0)                                               |
| Strings       | "Yok belajar Python"     | Represents sequences of characters enclosed in single or double quotes                                        |
| Integer       | 25 or 1209               | Represents whole numbers without a fractional component                                                       |
| Floats        | 3.14 or 0.99             | Represents numbers with decimal points or fractional components                                               |
| Hexadecimal   | 9a or 1d3                | Represents numbers in the base-16 (hex) format                                                               |
| Complex       | 1 + 5j                   | Represents numbers with both real and imaginary parts                                                       |
| List          | ['xyz', 786, 2.23]       | Represents an ordered collection of elements that can be of different data types. Lists are mutable, allowing modifications to the contents.  |
| Tuples        | ('xyz', 768, 2.23)       | Represents an ordered collection of elements that can be of different data types. Tuples are immutable, meaning their contents cannot be changed. |
| Dictionary    | {'nama': 'Banz', 'id':2}  | Represents a collection of key-value pairs where each key is associated with a value.                             |

To try various data types, please try the `Python script` below.

```python
# Integer
my_integer = 10
print("Integer:", my_integer)

# Float
my_float = 3.14
print("Float:", my_float)

# String
my_string = "Hello, World!"
print("String:", my_string)

# Boolean
my_boolean = True
print("Boolean:", my_boolean)

# List
my_list = [1, 2, 3, 4, 5]
print("List:", my_list)

# Tuple
my_tuple = (6, 7, 8, 9, 10)
print("Tuple:", my_tuple)

# Dictionary
my_dictionary = {'name': 'BanZ', 'age': 20, 'country': 'USA'}
print("Dictionary:", my_dictionary)

# Set
my_set = {1, 2, 3, 4, 5}
print("Set:", my_set)

# None
my_none = None
print("None:", my_none)
```

# Python variables

In Python, variables are used to store and manipulate data. A variable is a name that represents a value or an object in memory. It allows you to assign a value to a name, which can then be used throughout your program.

Here's an explanation of variables with an example:

Variable Declaration and Assignment:
You can declare a variable by giving it a name and assigning a value to it using the assignment operator (=). The value can be of any data type.

```python
# Variable declaration and assignment
x = 5
name = "John"
is_true = True
```

Variable Naming Rules :

`Variable names` must start with a letter or an underscore.
They can contain letters, digits, and underscores.
Variable names are case-sensitive, so age and Age are different variables.

```python
_count = 10
name1 = "Alice"
my_variable = 3.14

```
Variable Reassignment :

You can change the value of a variable by assigning a new value to it.

```python
x = 5
x = 10  # Reassigning x to a new value
```
Using Variables in Expressions :

Variables can be used in mathematical or logical expressions.

```python
x = 5
y = 3
sum = x + y
print(sum)  # Output: 8
```

Dynamic Typing :

Python is a dynamically typed language, meaning you don't need to explicitly declare the data type of a variable. The interpreter infers the type based on the assigned value.

```python
x = 5      # x is an integer
x = "Hello"  # x is now a string
```

Variable Scope :

Variables have a scope, which determines where they can be accessed. Variables defined inside a function have local scope and are only accessible within that function. Variables defined outside any function have global scope and can be accessed throughout the program.

```python
x = 10  # Global variable

def my_function():
    y = 5  # Local variable
    print(x + y)  # Accessing global and local variables

my_function()  # Output: 15
```

Variables are fundamental for storing and manipulating data in Python. They allow you to work with different types of information, perform calculations, and track state in your programs.

# Python operators

Operators are constructs that can manipulate the values ​​of operands.

For example, the operation `3 + 2 = 5`. Here `3` and `2` are the operands and `+` are the operators.

The Python programming language supports various operators, including :

* `Arithmetic Operators`

| Operator        | Example       | Explanation                                                                             |
|-----------------|---------------|-----------------------------------------------------------------------------------------|
| Addition        | 1 + 3         | Adds up the value of each operand or number                                             |
| Subtraction     | 4 - 1         | Subtracts the value of the operand on the right from the operand on the left             |
| Multiplication  | 2 * 4         | Multiplies operands/numbers                                                             |
| Division        | 10 / 5        | Divides the operand on the left by the operand on the right                             |
| Modulo          | 11 % 2        | Gets the remainder of the division of the operand on the left by the operand on the right |
| Exponentiation  | 8 ** 2        | Raises the operand on the left to the power of the operand on the right                  |
| Floor Division  | 10 // 3       | Performs division and discards the decimal part of the result                           |

Below is an example of using `Arithmetic Operators` in the Python programming language.

```python
# Arithmetic Operators Example

# Addition
num1 = 10
num2 = 5
sum = num1 + num2
print("Addition:", sum)  # Output: 15

# Subtraction
difference = num1 - num2
print("Subtraction:", difference)  # Output: 5

# Multiplication
product = num1 * num2
print("Multiplication:", product)  # Output: 50

# Division
quotient = num1 / num2
print("Division:", quotient)  # Output: 2.0

# Floor Division
floor_division = num1 // num2
print("Floor Division:", floor_division)  # Output: 2

# Modulo
remainder = num1 % num2
print("Modulo:", remainder)  # Output: 0

# Exponentiation
power = num1 ** num2
print("Exponentiation:", power)  # Output: 100000
```

* `Comparison Operators`

Comparison operators are used to compare a value of each operand.

| Operator               | Example       | Explanation                                                                                                  |
|------------------------|---------------|--------------------------------------------------------------------------------------------------------------|
| Equal to               | 1 == 1        | Evaluates to True if each operand has the same value                                                        |
| Not equal to           | 2 != 2        | Evaluates to True if the operands have different values                                                      |
| Not equal to           | 2 <> 2        | Evaluates to True if the operands have different values (alternative syntax)                                 |
| Greater than           | 5 > 3         | Evaluates to True if the value of the left operand is greater than the value of the right operand           |
| Less than              | 5 < 3         | Evaluates to True if the value of the left operand is less than the value of the right operand              |
| Greater or equal to    | 5 >= 3        | Evaluates to True if the value of the left operand is greater than or equal to the value of the right operand |
| Less or equal to       | 5 <= 3        | Evaluates to True if the value of the left operand is less than or equal to the value of the right operand    |

Below is an example of using comparation Operators in the Python programming language

```python
# Comparison Operators Example

# Equal to
num1 = 10
num2 = 5
print("Equal to:", num1 == num2)  # Output: False

# Not equal to
print("Not equal to:", num1 != num2)  # Output: True

# Greater than
print("Greater than:", num1 > num2)  # Output: True

# Less than
print("Less than:", num1 < num2)  # Output: False

# Greater than or equal to
print("Greater than or equal to:", num1 >= num2)  # Output: True

# Less than or equal to
print("Less than or equal to:", num1 <= num2)  # Output: False
```

* `Assignment Operators`

The assignment operator is used to assign or modify a value to a variable.

| Operator          | Example     | Explanation                                                                                   |
|-------------------|-------------|-----------------------------------------------------------------------------------------------|
| Assignment        | a = 1       | Assigns the value on the right to the variable on the left                                    |
| Add and assign    | a += 2      | Assigns the variable's value as the sum of its current value and the value on the right       |
| Subtract and assign | a -= 2     | Assigns the variable's value as the difference between its current value and the value on the right |
| Multiply and assign | a *= 2     | Assigns the variable's value as the product of its current value and the value on the right  |
| Divide and assign | a /= 4      | Assigns the variable's value as the quotient of its current value divided by the value on the right |
| Modulo and assign | a %= 3       | Assigns the variable's value as the remainder of its current value divided by the value on the right |
| Exponentiation and assign | a **= 3 | Assigns the variable's value as its current value raised to the power of the value on the right |
| Floor division and assign | a //= 3 | Assigns the variable's value as the result of dividing its current value by the value on the right, discarding the decimal part |

* `Operator Execution Priority in Python`

Of all the operators above, each has a priority order which later the first priority will be carried out first, and so on until the last priority.

| Operator  | Category    | Explanation                                           |
|-----------|-------------|-------------------------------------------------------|
| **        | Arithmetic  | Exponentiation (raising to the power)                 |
| ~, +, -   | Bitwise     | Bitwise complement, Unary positive and negative       |
| *, /, %, // | Arithmetic | Multiplication, Division, Modulo, Floor division      |
| +, -      | Arithmetic  | Addition, Subtraction                                  |
| >>, <<    | Bitwise     | Right shift, Left shift                               |
| &         | Bitwise     | Bitwise AND                                           |
| ^         | Bitwise     | Bitwise XOR                                           |
| <=, <, >, >= | Comparison | Less than or equal to, Less than, Greater than, Greater than or equal to |
| <>, ==, != | Comparison  | Not equal to, Equal to                                 |
| =, %=, /=, //=, -=, +=, *=, **= | Assignment | Assignment with arithmetic operations             |
| is, is not | Identity    | Object identity comparison                            |
| in, not in | Membership  | Membership test (check if a value exists in a sequence) |
| not, or, and | Logic      | Logical NOT, Logical OR, Logical AND                  |


# Python condition

* `If condition`

Decision making (if conditions) is used to anticipate conditions that occur when the program is running and determine what actions will be taken according to the conditions.

In python there are several statements/conditions including `if, else, and elif Conditions` if are used to execute code if the condition evaluates to true `True`.

If the condition evaluates to false Falsethen the statement/condition ifwill not be executed.

Below is an example of using the if condition in Python

```python
# If Condition Example

# Define a variable
num = 10

# Check if the number is positive
if num > 0:
    print("The number is positive.")

# Check if the number is even
if num % 2 == 0:
    print("The number is even.")
```

* `If-Else condition`

Decision making (if else condition) is not only used to determine what action will be taken according to the condition, but also used to determine what action will be taken/executed if the condition does not match.

In python there are several statements/conditions including if, else and elif The if condition is used to execute code if the condition evaluates to true.

The if else condition is a condition where if the statement is true `True` then the code in the if will be executed, but if it is false `False` then the code inside the else will be executed.

Below is an example of using the if else condition in Python

```python
# If-Else Condition Example

# Define a variable
num = 10

# Check if the number is positive
if num > 0:
    print("The number is positive.")
else:
    print("The number is not positive.")
```
* `Elif condition`

Decision making (if elif condition) is a logical continuation/branching of the `if condition`. With elif we can create program code that will select several possibilities that can occur. Almost the same as the `else` condition, the difference between the `elif` conditions can be many and not just one.

Below is an example of using the elif condition in Python

```python
# Elif Condition Example

# Define a variable
score = 85

# Determine the grade based on the score
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

# Print the grade
print("Grade:", grade)

```

# Loop Python

In general, statements in a programming language will be executed sequentially. The first statement in a function is executed first, followed by the second, and so on. But there will be situations where you have to write a lot of code, which is a lot of code. If done manually, you will only waste energy by writing hundreds or even thousands of codes. For that you need to use repetition in the Python programming language.

In the Python programming language repetition is divided into 3 parts, namely:

* `While Loop`

* `For Loop`

* `Nested Loop`

<-> `While Loop` <->

While loop repetition in the Python programming language statement is executed many times as long as the condition evaluates to `true or True`.

Below is an example of using the While Loop loop.

```python
# While Loop Example

# Countdown from 5 to 1
count = 5
while count >= 1:
    print(count)
    count -= 1

# Sum of numbers from 1 to 5
sum = 0
num = 1
while num <= 5:
    sum += num
    num += 1
print("Sum:", sum)
```

<-> `For Loop` <->

Looping `for` in Python has the ability to iterate over items of any order, such as `list` or `string`.

Below is an example of using a For Loop.

```python
# For Loop Example

# Iterate over a list
fruits = ["apple", "banana", "orange", "grape"]
for fruit in fruits:
    print(fruit)

# Iterate over a string
message = "Hello, World!"
for char in message:
    print(char)

# Iterate using range()
for num in range(1, 5):
    print(num)
```

<-> `Nested Loop` <->

The Python programming language allows the use of one loop inside another loop. The following section shows some examples to illustrate the concept.

Below is an example of using a Nested Loop.

```python
# Nested Loop Example

# Outer loop
for i in range(1, 4):
    # Inner loop
    for j in range(1, 4):
        print(i, j)

```

# Number Python

`Number` is a Python data type that stores numeric values. Number is an immutable data type. This means, changing the value of some data type will result in a newly allocated object.

The Number object is created when you assign a value to it. As an example : `angkaPertama = 1 angkaKedua = 33`

Python supports several Number data types including :

* Int
* Float
* Complex

Here are some examples of the Number data type in Python :

| Int   | Float          | Complex       |
|-------|----------------|---------------|
| 20    | 0.1            | 3.14j         |
| 300   | 1.20           | 35.j          |
| -13   | -41.2          | 3.12e-12j     |
| 020   | 32.23+e123     | .873j         |
| -0103 | -92.           | -.123+0J      |
| -0x212| -32.52e10      | 3e+123J       |
| 0x56  | 60.2-E13       | 4.31e-4j      |


* `Python Number Data Type Conversion`

In Python you can convert data types using functions. Below are some functions to convert the Python number data type.

`int(x)` to convert x to a plain integer.

`long(x)` to convert x to a long integer.

`float(x)` to convert x to a floating point number.

`complex(x)` to convert x to a complex number with a real part x and an imaginary part zero.

`complex(x, y)` to convert x and y to a complex number with a real part x and an imaginary part y. x and numeric expressions y.

* `Python Mathematical Functions`

In the Python programming language there are functions to perform mathematical calculations, here is the list :

| Name       | Use           | Explanation                                                              |
|------------|---------------|--------------------------------------------------------------------------|
| Absolute   | abs(x)        | The absolute value of x: (positive) is the distance between x and 0.      |
| Ceiling    | ceil(x)       | Ceiling of x: the smallest integer greater than or equal to x.            |
| Cmp        | cmp(x, y)     | -1 if x < y, 0 if x == y, or 1 if x > y. No longer available in Python 3. |
| Exponent   | exp(x)        | Exponent value of x: e^x.                                                |
| Fabs       | fabs(x)       | The absolute value of x.                                                 |
| Floor      | floor(x)      | Floor value of x: the largest integer less than or equal to x.            |
| Log        | log(x)        | Logarithm of x, for x > 0.                                                |
| Log 10     | log10(x)      | The base 10 logarithm of x, for x > 0.                                    |
| Max        | max(x1, x2,...)| Largest argument: the value closest to positive infinity.                 |
| Min        | min(x1, x2,...)| Least argument: the value closest to negative infinity.                   |
| Modf       | modf(x)       | The fractional and integer parts of x in a two-item tuple.                 |
| Pow        | pow(x, y)     | x raised to the power y.                                                  |
| Round      | round(x [,n]) | x is rounded to n digits from the decimal point.                           |
| Square root| sqrt(x)       | Square root of x for x > 0.                                               |

* `Python's Random Number Function`

Random numbers are used for gaming, simulation, testing, security and privacy applications. 

Python includes the following commonly used functions. Here is the list:

| Name       | Use                     | Explanation                                                           |
|------------|-------------------------|-----------------------------------------------------------------------|
| Choice     | choice(seq)             | Selects a random item from a list, tuple, or string.                   |
| RandRange  | randrange([start,] stop [,step]) | Returns a randomly selected element from the range (start, stop, step). |
| Random     | random()                | Returns a random float r, such that 0 <= r < 1.                        |
| Seed       | seed([x])               | Sets the initial integer value used in generating random numbers.      |
| Shuffle    | shuffle(lst)            | Shuffles the elements in a list in-place.                              |
| Floor      | floor(x)                | Returns the largest integer not greater than x.                        |
| Uniform    | uniform(x, y)           | Returns a random float r, such that x <= r < y.                        |

* `Python Trigonometry Functions`

Python includes the following functions which perform trig calculations. 

Here is the list:

| Name      | Usage                | Explanation                                               |
|-----------|----------------------|-----------------------------------------------------------|
| Acos      | acos(x)              | Returns the arc cosine of x, in radians.                   |
| Asin      | asin(x)              | Returns the arc sine of x, in radians.                     |
| Atan      | atan(x)              | Returns the arc tangent of x, in radians.                  |
| Atan2     | atan2(y, x)          | Returns the arc tangent of y/x, in radians.                |
| Cos       | cos(x)               | Returns the cosine of x radians.                           |
| Hypot     | hypot(x, y)          | Returns the Euclidean norm, sqrt(x^2 + y^2).               |
| Sin       | sin(x)               | Returns the sine of x radians.                             |
| Tan       | tan(x)               | Returns the tangent of x radians.                          |
| Degrees   | degrees(x)           | Converts angle x from radians to degrees.                  |
| Radians   | radians(x)           | Converts angle x from degrees to radians.                  |

* `Python Mathematical Constants`

This module also defines two mathematical constants. 

Here is the list:

| Name    | Use  | Explanation                        |
|---------|------|------------------------------------|
| Pi      | pi   | The mathematical constant Pi        |
| E       | e    | Mathematical constant e             |

# Python strings

`Strings` are the most popular type in programming languages. We can make it just by enclosing the characters in quotes. Python treats single quotes the same as double quotes. Creating strings is as easy as assigning a value to a variable.

Below is a simple example of a string in the Python programming language.

```python
print("Hello World")
```

* `Accessing Values ​​in a String`

Python doesn't use the semicolon character type; It is treated as a string of length one, so it is also considered a substring.

To access substrings, use square brackets to slice along with an index or index to get your substring. 

As an example :

```python
# Accessing Substrings Example

# Define a string
text = "Hello, World!"

# Accessing a single character
char = text[0]
print("Single character:", char)  # Output: H

# Accessing a substring
substring = text[7:12]
print("Substring:", substring)  # Output: World

# Accessing a substring from a specific index to the end
substring2 = text[7:]
print("Substring to the end:", substring2)  # Output: World!
```

In the above code, we have a string text containing the value `Hello, World!`. Here's how we access substrings using square brackets:

Accessing a Single Character:
We can access a single character in a string by specifying its index within square brackets. In the example, `text[0]` retrieves the character at index 0, which is `H`. The character is then assigned to the variable char and printed.

Accessing a Substring:
To access a substring, we use a slicing operation within the square brackets. In the example, `text[7:12]` retrieves the characters from index 7 to 11 (exclusive), resulting in the substring "World". The substring is assigned to the variable substring and printed.

Accessing a Substring from a Specific Index to the End:
If we omit the end index in the slicing operation, it defaults to the end of the string. In the example, `text[7:]` retrieves the characters starting from index 7 to the end of the string, resulting in the substring `World!`. The substring is assigned to the variable substring2 and printed.

By using square brackets and providing appropriate indices or slicing operations, you can access specific characters or substrings within a string.


* `Updating Strings

You can `update` an existing string by `(re)` assigning a variable to another string. The new value can be associated with the previous value or to a completely different string. 

As an example : 

```python
# Updating an Existing String Example

# Define an initial string
greeting = "Hello"

# Update the string by concatenating with another string
greeting += ", World!"
print("Updated String:", greeting)  # Output: Hello, World!

# Update the string with a completely different value
greeting = "Hi there!"
print("Updated String:", greeting)  # Output: Hi there!
```

* `Escape Characters / Python Escape Characters`

Below is a table of the list of escape characters or non-printable characters that can be represented/written with the prefix backslash notation.

| Backslash Notation | Hexadecimal Characters | Explanation                                |
|--------------------|-----------------------|--------------------------------------------|
| \a                 | 0x07                  | Bells or alerts                            |
| \b                 | 0x08                  | Backspace                                  |
| \cx                |                       | Control-x                                  |
| \C-x               |                       | Control-x                                  |
| \e                 | 0x1b                  | Escape                                     |
| \f                 | 0x0c                  | Formfeed                                   |
| \M-\C-x            |                       | Meta-Control-x                             |
| \n                 | 0x0a                  | Newline                                    |
| \nnn               |                       | Octal notation, where n is in the range 0-7 |
| \r                 | 0x0d                  | Carriage returns                           |
| \s                 | 0x20                  | Space                                      |
| \t                 | 0x09                  | Tab                                        |
| \v                 | 0x0b                  | Vertical tabs                              |
| \x                 |                       | Character x                                |
| \xnn               |                       | Hexadecimal notation, where n is in the range 0-9, a-f, or A-F |

* `Python String Special Operators`

Assuming the string variable is `Learn` and the variable b is 'Python', then below are the operators that can be used on both strings in that variable. `a = Learn, b = Python`

Here is a list of special string operators in Python:

| Operator | Example Usage | Explanation                                          |
|----------|---------------|------------------------------------------------------|
| +        | a + b         | Concatenation - Appends values on both sides of the operator |
| *        | a*2           | Repetition - Creates a new string by concatenating multiple copies of the same string |
| []       | a[1]          | Slice - Returns the character at the given index     |
| [ : ]    | a[1:4]        | Range Slice - Returns characters from the given range |
| in       | B in a        | Membership - Returns true if there are any characters in the given string |
| not in   | Z not in a    | Membership - Returns true if the character is not in the given string |
| r/R      | print r'\n'   | Raw String - Suppresses the actual meaning of the Escape character |
| %        | -             | Format - Performs string formatting                    |

* `Python String Format Operators`

One of Python's coolest features is the format string operator `%`. This operator is unique to strings and makes the package have functions from C's printf() family. 

Here's a simple example of this : `print ("My name is %s and weight is %d kg!" % ('Zara', 21))`

Here is a complete list of symbols that can be used with `%` :

| Operator | Explanation                                          |
|----------|------------------------------------------------------|
| %c       | Character                                            |
| %s       | Convert string via str() before formatting           |
| %i       | Regarded as a decimal integer                        |
| %d       | Regarded as a decimal integer                        |
| %u       | Unsigned decimal integers                            |
| %o       | Octal integer                                        |
| %x       | Hexadecimal integer (lowercase)                      |
| %X       | Hexadecimal (uppercase) integer                      |
| %e       | Exponential notation (with lowercase 'e')            |
| %E       | Exponential notation (with uppercase 'E')            |
| %f       | Real floating point numbers                          |
| %g       | Which is shorter than %f and %e                      |
| %G       | Shorter than %f and %E                               |


# `Triple Quotes Python`

Python triple quotes are used by allowing strings to be written across multiple lines, including verb NEWLINEs, TABs, and other special characters. The syntax for triple quotes consists of three single or double quotes written in a row : 

Here is an example:

```python
kutipantiga = """this is a long string that is made up of
several lines and non-printable characters such as
TAB ( \t ) and they will show up that way when displayed.
NEWLINEs within the string, whether explicitly given like
this within the brackets [ \n ], or just a NEWLINE within
the variable assignment will also show up.
"""
print (kutipantiga)
```

# `Python Unicode Strings`

As of Python 3, all strings are represented in Unicode. Whereas Python 2 is stored internally as `8-bit ASCII`, it requires an `u` attachment to make it Unicode. But this is no longer needed now. :

Built-in String Methods

Python includes the following built-in methods for manipulating strings

| Method             | Explanation                                                                                              |
|--------------------|----------------------------------------------------------------------------------------------------------|
| capitalize()       | Capitalizes the first letter of the string                                                               |
| center(width, fillchar) | Returns a string covered with fillchar with the original string centered on the total column width    |
| count(str, beg=0, end=len(string)) | Counts the number of times str occurs in a string or in a substring of a string if start index beg and end index end are given |
| decode(encoding='UTF-8', errors='strict') | String decoding uses the codec listed for encoding. Default encoding to default string encoding |
| encode(encoding='UTF-8', errors='strict') | Returns the string-encoded version of the string; On errors, the default is to raise a ValueError unless the error is assigned with 'ignore' or 'replace' |
| endswith(suffix, beg=0, end=len(string)) | Specifies whether a string or a substring of a string (if starting index is invoked and ending index end is given) ends with a suffix; Returns true if true and false |
| expandtabs(tabsize=8) | Expands tabs in a string to multiple spaces; Defaults to 8 spaces per tab if tabsize is not available |
| find(str, beg=0, end=len(string)) | Determine if str occurs in a string or in a substring of a string if start index beg and end index end return index if found and -1 otherwise |
| index(str, beg=0, end=len(string)) | Same as find(), but raises an exception if str is not found |
| isalnum() | Returns true if the string has at least 1 character and all characters are alphanumeric and false otherwise |
| isalpha() | Returns true if the string has at least 1 character and all characters are alphabetical and false otherwise |
| isdigit() | Returns true if the string contains only digits and false otherwise |
| islower() | Returns true if the string has at least 1 cased character and all cased characters are in lowercase and false otherwise |
| isnumeric() | Returns true if the unicode string contains only numeric characters and false otherwise |
| isspace() | Returns true if the string contains only space characters and false otherwise |
| istitle() | Returns true if the true string is "titlecased" and false otherwise |
| isupper() | Returns true if the string has at least one cased character and all cased characters are in uppercase and false otherwise |
| join(seq) | Merges (concatenates) a string representation of the elements in seq sequence into a string, with a separator string |
| len(string) | Returns the length of the string |
| ljust(width[, fillchar]) | Returns a space-padded string with the original string left justified to the total width column |
| lower() | Converts all uppercase letters in a string to lowercase |
| lstrip() | Removes all leading spaces in the string |
| maketrans() | Returns a translation table for use in the translate function |
| max(str) | Returns the alphabetical characters of the string str |
| min(str) | Returns the min alphabetical characters from the string str |
| replace(old, new[, max]) | Replaces all old occurrences in a string with new or max occurrences if max is given |
| rfind(str, beg=0, end=len(string)) | Same as find(), but search backwards in the string |
| rindex(str, beg=0, end=len(string)) | Same as index(), but search backwards in the string |
| rjust(width[, fillchar]) | Returns a space-coated string with the original

# List Python

In the Python programming language, the most basic data structures are sequences or lists. Each successive element will be assigned a position number or index. The first index in the list is zero, the second index is one and so on.

Python has six built-in order types, but the most common are lists and tuples. There are several things you can do with any type of list. These operations include indexing, slicing, adding, multiplying, and checking membership. Additionally, Python has built-in functions to find the length of a list and to find its largest and smallest elements.

* `Create Python Lists`

List is the most versatile data type available in the Python language, which can be written as a comma-separated list of values ​​(items) between square brackets. The important thing about lists is that the items in the list cannot be of the same type.

Creating a list is very simple, just enter the various comma-separated values ​​between the square brackets. 

Below is a simple example of creating a list in Python.

```python
# Creating a List Example

# Create an empty list
empty_list = []

# Create a list with values
fruits = ["apple", "banana", "orange", "grape"]

# Print the lists
print("Empty List:", empty_list)
print("Fruits List:", fruits)
```

* `Access Values ​​in a Python List`

To access a value in a python list, use square brackets to slice along with the index or indexes to get the values ​​available at that index.

Here is an example of how to access values ​​inside a python list :

```python
# Accessing Values in a List Example

# Create a list of numbers
numbers = [10, 20, 30, 40, 50]

# Accessing values by index
print("First number:", numbers[0])  # Output: 10
print("Third number:", numbers[2])  # Output: 30

# Accessing values using negative index
print("Last number:", numbers[-1])  # Output: 50
print("Second last number:", numbers[-2])  # Output: 40

# Accessing values using slicing
print("Slice of numbers:", numbers[1:4])  # Output: [20, 30, 40]
```

* `Update Values ​​in a Python List`

You can update one or more values ​​in a list by providing a stub to the left of the assignment operator, and you can add values ​​to a list with the `append() method`. 

As an example :

```python
# Updating and Adding Values in a List Example

# Create a list of names
names = ["Alice", "Bob", "Charlie", "Dave"]

# Update a value in the list
names[2] = "Charlie Brown"
print("Updated List:", names)  # Output: ['Alice', 'Bob', 'Charlie Brown', 'Dave']

# Add a value to the end of the list
names.append("Eve")
print("Updated List:", names)  # Output: ['Alice', 'Bob', 'Charlie Brown', 'Dave', 'Eve']
```

* `Delete Values ​​in a Python List`

To remove values ​​inside a python list, you can use one of the del statements if you know exactly the element you are removing. You can use the `remove()` method if you don't know exactly which items to remove. 

As an example :

```py
# Deleting Values in a List Example

# Create a list of numbers
numbers = [10, 20, 30, 40, 50]

# Delete a value by index
del numbers[2]
print("Updated List:", numbers)  # Output: [10, 20, 40, 50]

# Delete a value by value
numbers.remove(20)
print("Updated List:", numbers)  # Output: [10, 40, 50]

# Delete multiple values by slicing
del numbers[1:3]
print("Updated List:", numbers)  # Output: [10, 50]
```

<->`Basic Operations on Python Lists`<->

Python lists respond to the + and * operators like strings; That means concatenation and looping here also apply, except that the result is a new list, not a String.

In fact, lists respond to all the common ordering operations we used on String in the previous chapter. Below is a table listing the basic operations on list python.

| Python Expression                            | Results                               | Explanation        |
| -------------------------------------------- | ------------------------------------- | ------------------ |
| len([1, 2, 3, 4])                          | 4                                   | Length             |
| [1, 2, 3] + [4, 5, 6]                      | [1, 2, 3, 4, 5, 6]                 | Concatenation      |
| ['Halo!'] * 4                              | ['Halo!', 'Halo!', 'Halo!', 'Halo!'] | Repetition         |
| 2 in [1, 2, 3]                             | True                                | Membership         |
| for x in [1,2,3] : print (x,end = ' ')      | 1 2 3                              | Iteration          |


<-> `Indexing, Slicing and Matrix in List Python` <->

Because lists are sequences, indexing and slicing work the same way for lists as they do for Strings.

Assuming the following inputs:
```
L = ['C++'', 'Java', 'Python']
```

| Python Expression | Results           | Explanation                       |
| ----------------- | ----------------- | --------------------------------- |
| `L[2]`            | `'Python'`        | Offset starts from zero            |
| `L[-2]`           | `'Java'`          | Negative: count from the right     |
| `[1:]`            | `['Java', 'Python']` | Slicing took part                  |

<-> `Build-in Methods and Functions in List Python` <->

Python includes the following built-in functions :

| Python Function   | Explanation                                   |
| ----------------- | --------------------------------------------- |
| `cmp(list1, list2)` | No longer available with Python 3              |
| `len(list)`        | Returns the total length of the list           |
| `max(list)`        | Returns the item from the list with the max value |
| `min(list)`        | Returns the item from the list with the min value |
| `list(seq)`        | Turn tuples into lists                         |

Python includes the following built-in methods

| Python Method               | Explanation                                                          |
| --------------------------- | -------------------------------------------------------------------- |
| `list.append(obj)`          | Adds an `obj` object to the list                                      |
| `list.count(obj)`           | Returns the number of times `obj` occurs in the list                  |
| `list.extend(seq)`          | Adds the contents of `seq` to the list                                |
| `list.index(obj)`           | Returns the lowest index in the list where `obj` appears              |
| `list.insert(index, obj)`   | Inserts `obj` object into the list at the specified `index`           |
| `list.pop(obj = list[-1])`  | Removes and returns the last object from the list or the specified `obj` |
| `list.remove(obj)`          | Removes `obj` from the list                                           |
| `list.reverse()`            | Reverses the order of objects in the list in-place                    |
| `list.sort([func])`         | Sorts the objects in the list, using the provided comparison function if given |

