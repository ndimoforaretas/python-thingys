---
layout: post
title: 100 Days Of Python - Day 6
date: 2023-08-19 18:44 +0000
categories: [Python Tutorial, Day 6]
tags: [functions, indentation, the while loop, day 6]
---

## Day 6

## Python Functions

A function is a block of code that performs a specific task. It is a reusable piece of code that can be called from anywhere in your program.

### Defining a function

To define a function, use the `def` keyword followed by the function name and parentheses `()`.

```python
def my_function():
    print("Hello World!")
```

### Calling a function

To call a function, use the function name followed by parentheses `()`.

```python
def my_function():
    print("Hello World!")

my_function()
```

### Passing arguments to a function

You can pass arguments to a function by putting them inside the parentheses `()`.

```python
def my_function(name):
    print("Hello " + name + "!")
```

### Returning values from a function

You can return values from a function using the `return` keyword.

```python
def my_function(name):
    return "Hello " + name + "!"

print(my_function("World"))
```

### Default arguments

You can set default values for arguments in a function by using the `=` sign.

```python
def my_function(name="World"):
    return "Hello " + name + "!"

print(my_function())
```

### Indentation

Python uses indentation to indicate blocks of code.
The indentation level must be consistent throughout the program.

{: .prompt-warning}

> **In python, it is recommended to use 4 spaces for indentation.**

```python
def my_function():
    print("Hello World!")
```

- The following code shows how an if else statement is indented:

```python
if True:
    print("Hello World!")
else:
    print("Goodbye World!")
```

## The While Loop

The while loop is used to execute a block of code as long as a condition is true.

### Syntax

```python
while condition:
    # code to be executed
```

### Example

```python
i = 0

while i < 10:
    print(i)
    i += 1

print("Done!")

# Output:
# 0
# 1
# 2
# 3

# ...

# 9
# Done!
```
