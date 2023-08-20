---
layout: post
title: 100 Days Of Python - Day 10
date: 2023-08-20 05:34 +0000
categories: [Python Tutorial, Day 10]
tags:
  [
    functions with outputs,
    multiple return values,
    days in month,
    while loops,
    flags,
    recursion,
    calculator,
    day 10,
  ]
---

## Day 10

### Functions with Outputs

```python
def format_name(f_name, l_name):
    formatted_f_name = f_name.title()
    formatted_l_name = l_name.title()
    return f"{formatted_f_name} {formatted_l_name}"

print(format_name("jACk", "bLAck"))

# Output:
# Jack Black
```

### Multiple Return Values

```python
def format_name(f_name, l_name):
    if f_name == "" or l_name == "":
        return "You didn't provide valid inputs."
    formatted_f_name = f_name.title()
    formatted_l_name = l_name.title()
    return f"Result: {formatted_f_name} {formatted_l_name}"

print(format_name(input("What is your first name? "), input("What is your last name? ")))

# Output:
# What is your first name? jack
# What is your last name? black
# Result: Jack Black
```

### Days in Month

```python
def is_leap(year):
    if year % 4 == 0:
        if year % 100 == 0:
            if year % 400 == 0:
                return True
            else:
                return False
        else:
            return True
    else:
        return False

def days_in_month(year, month):
    if month > 12 or month < 1:
        return "Invalid month."
    if month == 2 and is_leap(year):
        return 29
    month_days = [
        31,
        28,
        31,
        30,
        31,
        30,
        31,
        31,
        30,
        31,
        30,
        31,
    ]
    return month_days[month - 1]

year = int(input("Enter a year: "))
month = int(input("Enter a month: "))
days = days_in_month(year, month)
print(days)

# Output:
# Enter a year: 2020
# Enter a month: 2
# 29
```

### While loops, flags, and recursion

**1. while loops**

- while loops are used to execute a block of code as long as a condition is true.

- syntax:

```python
# while condition:
#     # code to be executed

# example:

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
# 4


# ...

# 9
# Done!
```

**2. flags**

- flags are used to control the flow of a program.

- example:

```python
should_continue = True

while should_continue:
    print("Hello World!")
    if input("Do you want to continue? ") == "no":
        should_continue = False

# Output:
# Hello World!
# Do you want to continue? yes
# Hello World!
# Do you want to continue? yes
# Hello World!
# Do you want to continue? no

# recursion
```

**3. recursion**

- recursion is when a function calls itself.
- example:

```python
def add(n):
    if n == 1:
        return 1
    else:
        return n + add(n - 1)

print(add(5))

# Output:
# 15
```

### Calculator

```python
# art.py

logo = """
 _____________________
|  _________________  |
| | Pythonista   0. | |  .----------------.  .----------------.  .----------------.  .----------------.
| |_________________| | | .--------------. || .--------------. || .--------------. || .--------------. |
|  ___ ___ ___   ___  | | |     ______   | || |      __      | || |   _____      | || |     ______   | |
| | 7 | 8 | 9 | | + | | | |   .' ___  |  | || |     /  \     | || |  |_   _|     | || |   .' ___  |  | |
| |___|___|___| |___| | | |  / .'   \_|  | || |    / /\ \    | || |    | |       | || |  / .'   \_|  | |
| | 4 | 5 | 6 | | - | | | |  | |         | || |   / ____ \   | || |    | |   _   | || |  | |         | |
| |___|___|___| |___| | | |  \ `.___.'\  | || | _/ /    \ \_ | || |   _| |__/ |  | || |  \ `.___.'\  | |
| | 1 | 2 | 3 | | x | | | |   `._____.'  | || ||____|  |____|| || |  |________|  | || |   `._____.'  | |
| |___|___|___| |___| | | |              | || |              | || |              | || |              | |
| | . | 0 | = | | / | | | '--------------' || '--------------' || '--------------' || '--------------' |
| |___|___|___| |___| |  '----------------'  '----------------'  '----------------'  '----------------'
|_____________________|
"""

# calculator.py

from art import logo

def add(n1, n2):
    return n1 + n2

def subtract(n1, n2):
    return n1 - n2

def multiply(n1, n2):
    return n1 * n2

def divide(n1, n2):
    return n1 / n2

operations = {
    "+": add,
    "-": subtract,
    "*": multiply,
    "/": divide,
}

def calculator():
    print(logo)
    num1 = float(input("What's the first number?: "))
    for symbol in operations:
        print(symbol)
    should_continue = True
    while should_continue:
        operation_symbol = input("Pick an operation: ")
        num2 = float(input("What's the next number?: "))
        calculation_function = operations[operation_symbol]
        answer = calculation_function(num1, num2)
        print(f"{num1} {operation_symbol} {num2} = {answer}")
        if input(f"Type 'y' to continue calculating with {answer}, or type 'n' to start a new calculation: ") == "y":
            num1 = answer
        else:
            should_continue = False
            calculator()

calculator()

# Output:
#  _____________________
# |  _________________  |
# | | Pythonista   0. | |
# | |_________________| |
# |  ___ ___ ___   ___  |
# | | 7 | 8 | 9 | | + | |
# | |___|___|___| |___| |
# | | 4 | 5 | 6 | | - | |
# | |___|___|___| |___| |
# | | 1 | 2 | 3 | | x | |
# | |___|___|___| |___| |
# | | . | 0 | = | | / | |
# | |___|___|___| |___| |
# |_____________________|
# What's the first number?: 5
# +
# -
# *
# /
# Pick an operation: +
# What's the next number?: 5
# 5.0 + 5.0 = 10.0
# Type 'y' to continue calculating with 10.0, or type 'n' to start a new calculation: y
# Pick an operation: *
# What's the next number?: 5
# 10.0 * 5.0 = 50.0
# Type 'y' to continue calculating with 50.0, or type 'n' to start a new calculation: n
#  _____________________
# |  _________________  |
# | | Pythonista   0. | |
# | |_________________| |
# |  ___ ___ ___   ___  |
# | | 7 | 8 | 9 | | + | |
# | |___|___|___| |___| |
# | | 4 | 5 | 6 | | - | |
# | |___|___|___| |___| |
# | | 1 | 2 | 3 | | x | |
# | |___|___|___| |___| |
# | | . | 0 | = | | / | |
# | |___|___|___| |___| |
# |_____________________|
# What's the first number?: 5
# +
# -
# *
# /
# Pick an operation: /
# What's the next number?: 0
# 5.0 / 0.0 = inf
# Type 'y' to continue calculating with inf, or type 'n' to start a new calculation: n
#  _____________________
# |  _________________  |

# ...
```
