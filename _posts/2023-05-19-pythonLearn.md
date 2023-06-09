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

`Comments` are code in Python scripts that are not executed or not run by the machine. Comments are only used to mark or provide written information on the script.

Comments are commonly used to let others understand what the script is doing. or to remind the programmer himself if one day he returns to edit the script.

To use your comment simply write a hash sign `#` followed by your comment or by using a string literal that opens and closes with """.

Below is an example of using comments in Python.

```python
# Ini adalah komentar

# Tulisan ini tidak akan dieksekusi

#komentar dengan tanda pagar hanya bisa digunakan
#untuk
#satu
#baris

"""
Penulisan Komentar lebih dari satu baris yaitu
dengan menggunakan kutip dua 3 kali dan
ditutup dengan kutip dua 3 kali juga
"""

print("Hello World") #ini juga komentar

#print("Welcome")

# komentar bisa berisi spesial karakter !@#$%^&\*(),./;'[]\

#mencetak nama
print("BanZ")

#mencetak angka/integer
print(123)
```

When you run the script above, you will see output in the form of `Hello World`, `BanZ` and `123`, because the posts/comments written are not executed.

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
#tipe data Boolean
print(True)

#tipe data String
print("Yok Belajar Python")
print('Belajar Python Sangat Menyenangkan')

#tipe data Integer
print(20)

#tipe data Float
print(3.14)

#tipe data Hexadecimal
print(9a)

#tipe data Complex
print(5j)

#tipe data List
print([1,2,3,4,5])
print(["satu", "dua", "tiga"])

#tipe data Tuple
print((1,2,3,4,5))
print(("satu", "dua", "tiga"))

#tipe data Dictionary
print({"nama":"Banz", 'umur':20})
#tipe data Dictionary dimasukan ke dalam variabel biodata
biodata = {"nama":"Banz", 'umur':21} #proses inisialisasi variabel biodata
print(biodata) #proses pencetakan variabel biodata yang berisi tipe data Dictionary
print(type(biodata)) #fungsi untuk mengecek jenis tipe data. akan tampil <class 'dict'> yang berarti dict adalah tipe data dictionary
```

# Python variables

`Variables` are memory locations that are reserved for storing values. This means that when you create a variable you reserve some space in memory. Variables store data that is carried out during program execution, which later the contents of these variables can be changed by certain operations on programs that use variables.

Variables can store various types of data. In Python programming, variables have dynamic properties, meaning that Python variables do not need to be declared with certain data types and Python variables can be changed when the program is run.

Writing Python variables itself also has certain rules, namely:

* The first character must be a letter or an underscore `_`
* The next character can be a letter, underscore `_` or number
* Characters in variable names are case-sensitive. This means that lowercase and uppercase letters are distinguished. For example, the variables `namaDepan` and `namadepan` are different variables.

To start creating variables in Python it's very easy, you simply write down the variable and then fill it with a value by adding an equals sign followed `=` by the value you want to enter.

Below is an example of using variables in the Python programming language

```python
#proses memasukan data ke dalam variabel
nama = "Arz BanZ"
#proses mencetak variabel
print(nama)

#nilai dan tipe data dalam variabel dapat diubah
umur = 20 #nilai awal
print(umur) #mencetak nilai umur
type(umur) #mengecek tipe data umur
umur = "dua puluh satu" #nilai setelah diubah
print(umur) #mencetak nilai umur
type(umur) #mengecek tipe data umur

namaDepan = "Er"
namaBelakang = "BanZ"
nama = namaDepan + " " + namaBelakang
umur = 22
hobi = "Computer"
print("Biodata\n", nama, "\n", umur, "\n", hobi)

#contoh variabel lainya
inivariabel = "Halo"
ini_juga_variabel = "Hai"
\_inivariabeljuga = "Hi"
inivariabel222 = "Bye"

panjang = 10
lebar = 5
luas = panjang \* lebar
print(luas)
```

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
#OPERATOR ARITMATIKA

#Penjumlahan
print(13 + 2)
mangga = 7
apel = 9
buah = mangga + apel #
print(buah)

#Pengurangan
hutang = 80000
bayar = 5000
sisaHutang = hutang - bayar
print("Sisa hutang Anda adalah ", sisaHutang)

#Perkalian
panjang = 20
lebar = 8
luas = panjang * lebar
print(luas)

#Pembagian
roti = 16
orang = 4
kuePerAnak = Roti / orang
print("Setiap orang akan mendapatkan bagian roti sebanyak ", rotiPerorang)

#Sisa Bagi / Modulus
bilangan1 = 15
bilangan2 = 5
hasil = bilangan1 % bilangan2
print("Sisa bagi dari bilangan ", bilangan1, " dan ", bilangan2, " adalah ", hasil)

#Pangkat
bilangan3 = 8
bilangan4 = 2
hasilPangkat = bilangan3 ** bilangan4
print(hasilPangkat)

#Pembagian Bulat
print(10//3)
#10 dibagi 3 adalah 3.3333. Karena dibulatkan maka akan menghasilkan nilai 3
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

Below is an example of using Arithmetic Operators in the Python programming language

```python
# SAMA DENGAN
print(1 == 1) # Hasilnya akan bernilai True karena satu sama dengan satu
print(1 == 2) # Hasilnya akan bernilai False karena satu tidak sama dengan dua

# TIDAK SAMA DENGAN
print(2 != 2) # Hasilnya akan bernilai False karena dua seharusnya sama dengan dua
print(2 != 3) # Hasilnya akan bernilai True karena dua tidak sama dengan tiga

# LEBIH BESAR DARI
print(5 > 3) # Hasilnya akan bernilai True karena lima lebih besar dari tiga

# LEBIH KECIL DARI
print(5 < 3) # Hasilnya akan bernilai False karena lima tidak lebih besar dari tiga

# LEBIH BESAR DARI SAMA DENGAN
print(5 >= 3) # Hasilnya akan bernilai True karena lima lebih besar dari sama dengan tiga

# LEBIH KECIL DARI SAMA DENGAN
print(5 <= 3) # Hasilnya akan bernilai False karena lima tidak lebih besar dari sama dengan tiga
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
#Kondisi if adalah kondisi yang akan dieksekusi oleh program jika bernilai benar atau TRUE

nilai = 9

#jika kondisi benar/TRUE maka program akan mengeksekusi perintah dibawahnya
if(nilai > 8):
    print("Sembilan Lebih Besar Dari Angka 8") # Kondisi Benar, Dieksekusi

#jika kondisi salah/FALSE maka program tidak akan mengeksekusi perintah dibawahnya
if(nilai > 20):
    print("Sembilan Lebih Besar Dari Angka Duapuluh") # Kondisi Salah, Maka tidak tereksekusi
```

From the example above, if the program is run it will print the string `Sembilan Lebih Besar Dari Angka Tujuh` once, namely in the first if. In both if statements evaluate to false, so the command `print("Sembilan Lebih Besar Dari Angka Sepuluh")` will not be executed.

* `If-Else condition`

Decision making (if else condition) is not only used to determine what action will be taken according to the condition, but also used to determine what action will be taken/executed if the condition does not match.

In python there are several statements/conditions including if, else and elif The if condition is used to execute code if the condition evaluates to true.

The if else condition is a condition where if the statement is true `True` then the code in the if will be executed, but if it is false `False` then the code inside the else will be executed.

Below is an example of using the if else condition in Python

```python
#Kondisi if else adalah jika kondisi bernilai TRUE maka akan dieksekusi pada if, tetapi jika bernilai FALSE maka akan dieksekusi kode pada else

nilai = 3
#Jika pernyataan pada if bernilai TRUE maka if akan dieksekusi, tetapi jika FALSE kode pada else yang akan dieksekusi.
if(nilai > 7):
    print("Selamat Anda Lulus")
else:
    print("Maaf Anda Tidak Lulus")
```

In the example above, if the program is run it will print a string `Maaf Anda Tidak Lulus` because the if statement is valuableFalse

* `Elif condition`

Decision making (if elif condition) is a logical continuation/branching of the `if condition`. With elif we can create program code that will select several possibilities that can occur. Almost the same as the `else` condition, the difference between the `elif` conditions can be many and not just one.

Below is an example of using the elif condition in Python

```python
#Contoh penggunaan kondisi elif

day = "Minggu"

if(day == "Senin"):
    print("Saya akan kuliah")
elif(day == "Selasa"):
    print("Saya akan kuliah")
elif(day == "Rabu"):
    print("Saya akan kuliah")
elif(day == "Kamis"):
    print("Saya akan kuliah")
elif(day == "Jumat"):
    print("Saya akan kuliah")
elif(day == "Sabtu"):
    print("Saya akan kuliah")
elif(day == "Minggu"):
    print("Saya akan libur")
```

In the example above, if the program is run it will print the string `Saya akan libur`.

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
#Contoh penggunaan While Loop
#Catatan: Penentuan ruang lingkup di Python bisa menggunakan tab alih-alih menggunakan tanda kurung

count = 0
while (count < 9):
  print ("The count is: ", count)
  count = count + 1

print ("Good bye!")
```

<-> `For Loop` <->

Looping `for` in Python has the ability to iterate over items of any order, such as `list` or `string`.

Below is an example of using a For Loop.

```python
#Contoh pengulangan for sederhana
angka = [1,2,3,4,5]
for x in angka:
  print(x)

#Contoh pengulangan for
buah = ["mangga", "apel", "jeruk"]
for makanan in buah:
  print ("Saya suka makan", makanan)
```

<-> `Nested Loop` <->

The Python programming language allows the use of one loop inside another loop. The following section shows some examples to illustrate the concept.

Below is an example of using a Nested Loop.

```python
#Contoh penggunaan Nested Loop
#Catatan: Penggunaan modulo pada kondisional mengasumsikan nilai selain nol sebagai True(benar) dan nol sebagai False(salah)

i = 2
while(i < 100):
  j = 2
while(j <= (i/j)):
  if not(i%j): break
  j = j + 1
  if (j > i/j) : print(i, " is prime")
    i = i + 1

print("Good bye!")
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
name = 'John Doe' message = "John Doe belajar bahasa python di Belajarpython"
print ("name[0]: ", name[0])
print ("message[1:4]: ", message[1:4])
```

When the above code is executed, it will produce the following results:

`name[0]: J message[1:4]: ohn`

* `Updating Strings

You can `update` an existing string by `(re)` assigning a variable to another string. The new value can be associated with the previous value or to a completely different string. 

As an example : 

```python
message = 'Hello World'
print ("Updated String :- ", message[:6] + 'Python')
```

When the above code is executed, it will produce the following results:

`Updated String :- Hello Python`

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
#Contoh sederhana pembuatan list pada bahasa pemrograman python
list1 = ['kimia', 'fisika', 1993, 2017]
list2 = [1, 2, 3, 4, 5 ]
list3 = ["a", "b", "c", "d"]
```

* `Access Values ​​in a Python List`

To access a value in a python list, use square brackets to slice along with the index or indexes to get the values ​​available at that index.

Here is an example of how to access values ​​inside a python list :

```python
#Cara mengakses nilai di dalam list Python

list1 = ['fisika', 'kimia', 1993, 2017]
list2 = [1, 2, 3, 4, 5, 6, 7 ]

print ("list1[0]: ", list1[0])
print ("list2[1:5]: ", list2[1:5])
```

After you execute the above code, the result will be as below:

```
list1[0]: fisika list2[1:5]: [2, 3, 4, 5]
```

* `Update Values ​​in a Python List`

You can update one or more values ​​in a list by providing a stub to the left of the assignment operator, and you can add values ​​to a list with the `append() method`. 

As an example :

```python
list = ['fisika', 'kimia', 1993, 2017]
print ("Nilai ada pada index 2 : ", list[2])

list[2] = 2001
print ("Nilai baru ada pada index 2 : ", list[2])
```

* `Delete Values ​​in a Python List`

To remove values ​​inside a python list, you can use one of the del statements if you know exactly the element you are removing. You can use the `remove()` method if you don't know exactly which items to remove. 

As an example :

```py
#Contoh cara menghapus nilai pada list python

list = ['fisika', 'kimia', 1993, 2017]

print (list)
del list[2]
print ("Setelah dihapus nilai pada index 2 : ", list)
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

