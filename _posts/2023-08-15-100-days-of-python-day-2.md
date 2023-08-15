---
layout: post
title: 100 Days Of Python - Day 2
date: 2023-08-15 08:23 +0000
categories: [Python Tutorial, Day 2]
tags:
  [
    python,
    data types,
    string,
    integer,
    float,
    boolean,
    type checking,
    bmi calculator,
    tip calculator,
  ]
---

# Python - Day 2

## Data Types

Data types are the building blocks of all languages.
They are the different types of data that we can use in our programs.

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

{: .prompt-info }

> Strings in Python are surrounded by either single quotation marks `' '`, or double quotation marks `" "`.

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

## Mathematical Operations in Python

```python
print(3 + 5) # 8 - Addition
print(7 - 4) # 3 - Subtraction
print(3 * 2) # 6 - Multiplication
print(6 / 3) # 2.0 - Division
print(2 ** 3) # 8 - Exponent
```

### PEMDAS (Order of Operations)

In Python, the order of operations is the same as in mathematics:

- **P**arentheses = `()`
- **E**xponents = `**`
- **M**ultiplication = `*`
- **D**ivision = `/`
- **A**ddition = `+`
- **S**ubtraction = `-`

```python
print(3 * 3 + 3 / 3 - 3) # 7.0 - 3 * 3 = 9, 3 / 3 = 1, 9 + 1 = 10, 10 - 3 = 7
print(3 * (3 + 3) / 3 - 3) # 3.0 - 3 + 3 = 6, 3 * 6 = 18, 18 / 3 = 6, 6 - 3 = 3
```

## BMI Calculator

### Instructions:

- Write a program that calculates the Body Mass Index (BMI) from a user's weight and height.
- The BMI is a measure of some's weight taking into account their height. e.g. If a tall person and a short person both weigh the same amount, the short person is usually more overweight.
- The BMI is calculated by dividing a person's weight (in kg) by the square of their height (in m):
- Warning you should convert the result to a whole number.

Example Input

- weight = 80
- height = 1.75

Example Output

- 80 ÷ (1.75 x 1.75) = 26

{: .prompt-tip }

> ### Hint
>
> 1. Check the data type of the inputs.
> 2. Try to use the exponent operator in your code.
> 3. Remember PEMDAS.
> 4. Remember to convert your result to a whole number (int).

### Solution

```python

height = input("enter your height in m: ")
weight = input("enter your weight in kg: ")

print(type(height)) # <class 'str'>
print(type(weight)) # <class 'str'>

bmi = int(weight) / float(height) ** 2
print(int(bmi)) # 26
```

## Number Manipulation and F Strings in Python

In python, you can use

- the `round()` function to round a number to a certain number of decimal places.

```python
print(round(8 / 3)) # 3
print(round(8 / 3, 2)) # 2.67 - round to 2 decimal places
print(round(8 / 3, 3)) # 2.667 - round to 3 decimal places
```

- the `//` operator to get the integer part of a division

```python
print(8 // 3) # 2
```

- the `%` operator to get the remainder of a division

```python
print(8 % 3) # 2
```

### F-Strings

- F-Strings are a new way to format strings in Python 3.6 and above.
- They allow you to put variables inside a string.
- You can use f-strings by putting an `f` before the opening quote of a string.
- Then you can put variables inside the string by using curly braces `{}`.

```python
score = 0
height = 1.8
isWinning = True

# f-String
print(f"your score is {score}, your height is {height}, you are winning is {isWinning}") # your score is 0, your height is 1.8, you are winning is True
```

## Life in Weeks

### Instructions

- Create a program using maths and f-Strings that tells us how many days, weeks, months we have left if we live until 90 years old.
- It will take your current age as the input and output a message with our time left in this format:

> You have x days, y weeks, and z months left.
> Where x, y and z are replaced with the actual calculated numbers.

{: .prompt-tip }

> ### Hint
>
> 1. There are 365 days in a year, 52 weeks in a year and 12 months in a year.
> 2. Try copying the example output into your code and replace the relevant parts so that the sentence is formated the same way.
> 3. Remember to use the `round()` function to round the final number of days, weeks and months. **Note** that the `round()` function will convert the float into an integer. **Hint** You will need to Google how to convert a float into an integer.
> 4. Your life span in years is calculated from your current age and the number 90.
> 5. Try running your code for different ages to calculate the number of days, weeks and months you have left to live.
> 6. **Bonus**: Format the numbers so that the output looks nicer. **Hint**: You will need to Google how to use the `f"{value:2d}"` syntax.

### Solution

```python
age = input("What is your current age? ")

years_left = 90 - int(age)
days_left = years_left * 365
weeks_left = years_left * 52
months_left = years_left * 12

message = f"You have {days_left} days, {weeks_left} weeks, and {months_left} months left."
print(message)
```

## Tip Calculator

### Instructions

- If the bill was $150.00, split between 5 people, with 12% tip.
- Each person should pay (150.00 / 5) \* 1.12 = 33.6
- Format the result to 2 decimal places = 33.60
- Tip: There are 2 ways to round a number. You might have to do some Googling to solve this.💪

{: .prompt-tip }

> ### Hint
>
> 1. Try to print the result of the division.
> 2. Try to print the result of the multiplication.
> 3. Try to print the result of the division.
> 4. Try to print the result of the multiplication.

### Solution

```python
print("Welcome to the tip calculator.")
total_bill = float(input("What was the total bill? $"))
tip_percentage = int(input("What percentage tip would you like to give? 10, 12, or 15? "))
number_of_people = int(input("How many people to split the bill? "))
bill_with_tip = total_bill * (1 + tip_percentage / 100)
bill_per_person = bill_with_tip / number_of_people
#final_amount = round(bill_per_person, 2) # round to 2 decimal places
final_amount = "{:.2f}".format(bill_per_person) # round to 2 decimal places

print(f"Each person should pay: ${final_amount}")
```
