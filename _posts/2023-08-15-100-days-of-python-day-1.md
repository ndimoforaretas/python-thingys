---
layout: post
title: 100 Days Of Python - Day 1
date: 2023-08-15 08:06 +0000
categories: [Python, Day 1]
tags: [python, printing, variables, variable naming] # TAG names should always be lowercase
---

# Python - Day 1

## Printing

```python
print("Hello World")
```

## Input

```python

print("Hello " + input("What is your name? "))
```

## String length

```python
print(len(input("What is your name? ")))
```

## Variables

To create a variable, you just have to give it a name and set it equal to a value.

```python
name = "Jack"
print(name)
```

### Variable naming rules

- Variables names can not start with a number.
- Variables can not contain spaces, use \_ instead.
- Variables can not contain any of these symbols:

      `:'",<>/?|\!@#%^&*~-+`

- It's considered best practice (PEP8) that names are lowercase with underscores instead of spaces. For example:
- snake_case instead of MACRO_CASE
- CapitalizedWords or CamelCase instead of PascalCase
- Avoid using special symbols like @, $, %, etc.
- Don't start a variable name with a digit.

## Challenge

```python
# Write a program that switches the values stored in the variables a and b.

# Warning. Do not change the code below. Your program should work for different inputs. e.g. any value of a and b.

# Example Input
a = input("a: ")
b = input("b: ")

# Example Output
# a: 3
# b: 5

# a: 5
# b: 3

####################################
# Don't change the code below 👇

c = a
a = b
b = c

# Don't change the code above 👆

####################################
#Write your code below this line 👇

print("a: " + a)
print("b: " + b)
```

## Challenge

```python
# Write a program that generates a band name based on the user's hometown and pet name.

print("Welcome to the Band Name Generator.")
city = input("What's name of the city you grew up in?\n")
pet = input("What's your pet's name?\n")
# Example Output
print("Your band name could be " + city + " " + pet)
```
