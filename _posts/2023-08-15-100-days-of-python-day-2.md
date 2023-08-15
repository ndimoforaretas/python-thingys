---
layout: post
title: 100 Days Of Python - Day 2
date: 2023-08-15 08:23 +0000
categories: [Python Tutorial, Day 2]
tags: [python, data types, string, integer, float, boolean, type checking]
---

# Python - Day 2

## Data Types

Data types are the building blocks of all languages. They are the different types of data that we can use in our programs.

Data types in Python include:

- **String** like "Hello World"
- **Integer** like 123 = All whole numbers positive and negative including 0 (without decimal point)
- **Float** like 3.14159
- **Boolean** like True or False
- **List** like [1, 2, 3]
- **Dictionary** like {'name': 'Jack', 'age': 23}
- **Tuple** like (1, 2, 3)
- **Set** like {1, 2, 3}
- **None**

### String

Strings are used to store text. Strings in Python are surrounded by either single quotation marks, or double quotation marks.

```python
print("Hello"[0]) # H
print("Hello"[4]) # o
```

### Integer

Integers are used to store whole numbers. Integers are positive and negative numbers without decimals.

```python
print(123 + 345) # 468
print(123_456_789) # 123456789
```

### Float

Floats are used to store numbers with decimals.

```python
print(3.14159) # 3.14159
```

### Boolean

Booleans are used to store True or False values.

```python
print(True) # True
print(False) # False
```

## Type Error, Type Checking and Type Conversion

### Type Error

If you try to combine a string with a number, Python will give you an error.

```python
num_char = len(input("What is your name? "))
print("Your name has " + num_char + " characters.") # TypeError: can only concatenate str (not "int") to str
```

- `TypeError: can only concatenate str (not "int") to str` means that you can only concatenate strings to strings, not integers to strings.

### Type Checking

You can check the type of a variable's value using the `type()` function.

```python
print(type(num_char)) # <class 'int'>
```

### Type Conversion

You can convert one data type to another using the following functions:

- `str()` converts to string
- `int()` converts to integer
- `float()` converts to float

```python
num_char = len(input("What is your name? ")) # this is an integer
# print("Your name has " + num_char + " characters.") # TypeError: can only concatenate str (not "int") to str
# we need to convert num_char to a string
new_num_char = str(num_char) # "50" this is a string
print("Your name has " + new_num_char + " characters.") # Your name has 50 characters.
```

## Challenge

```python
# Write a program that adds the digits in a 2 digit number. e.g. if the input was 35, then the output should be 3 + 5 = 8

# Warning. Do not change the code on lines 1-3. Your program should work for different inputs. e.g. any two-digit number.

# Example Input
two_digit_number = input("Type a two digit number: ")

print(type(two_digit_number)) # <class 'str'>
print(type(two_digit_number[0])) # <class 'str'>
print(type(two_digit_number[1])) # <class 'str'>
print(int(two_digit_number[0]) + int(two_digit_number[1])) # 8

# first_num = int(two_digit_number[0]);
# second_num = int(two_digit_number[1]);

# print(first_num + second_num)
```
