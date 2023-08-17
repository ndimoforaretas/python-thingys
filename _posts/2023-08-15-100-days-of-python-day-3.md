---
layout: post
title: 100 Days Of Python - Day 3
date: 2023-08-15 18:51 +0000
categories: [Python Tutorial, Day 3]
tags:
  [
    conditional statements,
    if/else statements,
    elif statements,
    nested if statements,
    logical operators,
    comparison operators,
    odd or even,
    love calculator,
    bmi calculator 2.0,
    leap year,
    pizza order,
    day 3,
  ]
---

## Day 3

- Conditional statements in Python are used to control the flow of the program. They are used to perform different actions based on different conditions.

### If/Else Statements

- The `if` statement is used to specify a block of code to be executed if a condition is `True`. If the condition is `False`, another block of code can be specified to be executed using the `else` statement.

```python
if condition:
    # code to be executed if condition is True
else:
    # code to be executed if condition is False
```

### Elif Statements

- The `elif` statement is used to specify a new condition if the previous conditions are `False`.
- The `elif` statement is used to avoid writing multiple `if` statements.

```python
if condition:
    # code to be executed if condition is True
elif condition:
    # code to be executed if condition is True
else:
    # code to be executed if condition is False
```

### Example

```python
print("Welcome to the rollercoaster!")
height = int(input("What is your height in cm? "))

if height >= 120:
    print("You can ride the rollercoaster!")
age = int(input("What is your age? "))
    if age < 12:
        print("Please pay $5.")
    elif age <= 18:
        print("Please pay $7.")
    else:
        print("Please pay $12.")
else:
    print("Sorry, you have to grow taller before you can ride.")
```

### Nested If Statements

- Nested `if` statements are `if` statements that are placed inside another `if` statement. They are used to test for multiple conditions.

```python
if condition:
    # code to be executed if condition is True
    if condition:
        # code to be executed if condition is True
    else:
        # code to be executed if condition is False
else:
    # code to be executed if condition is False
```

### Logical Operators

- Logical operators are used to combine conditional statements.

- `and` - Returns `True` if both statements are `True`
- `or` - Returns `True` if one of the statements is `True`
- `not` - Reverse the result, returns `False` if the result is `True`
- `in` - Returns `True` if a sequence with the specified value is present in the object
- `not in` - Returns `True` if a sequence with the specified value is not present in the object
- `is` - Returns `True` if both variables are the same object
- `is not` - Returns `True` if both variables are not the same object
- `==` - Returns `True` if both variables are equal
- `!=` - Returns `True` if both variables are not equal
- `>` - Returns `True` if the left operand is greater than the right operand
- `<` - Returns `True` if the left operand is less than the right operand
- `>=` - Returns `True` if the left operand is greater than or equal to the right operand
- `<=` - Returns `True` if the left operand is less than or equal to the right operand

### Comparison Operators

Comparison operators are used to compare two values.

- `==` - Equal
- `!=` - Not equal
- `>` - Greater than
- `<` - Less than
- `>=` - Greater than or equal to
- `<=` - Less than or equal to
- `is` - Returns `True` if both variables are the same object
- `is not` - Returns `True` if both variables are not the same object
- `in` - Returns `True` if a sequence with the specified value is present in the object
- `not in` - Returns `True` if a sequence with the specified value is not present in the object

### Example

```python
x = 5
y = 10

if x > y:
    print("x is greater than y")
elif x < y:
    print("x is less than y")
else:
    print("x is equal to y")

# Output: x is less than y
```

### Odd or Even

```python
number = int(input("Enter a number: "))
if number % 2 == 0:
    print("The number is even")
else:
    print("The number is odd")
```

### BMI Calculator 2.0

{:.prompt-info}

> This version of the BMI calculator is an update to the previous version.
>
> - It uses nested `if` statements to print different outputs depending on the BMI score.
> - After calculating the BMI, the program prints the user's BMI score and a message based on the BMI score. For example,
> - If the BMI is less than 18.5, the program prints `"Your BMI is 16, you are underweight."`
> - If the BMI is between 18.5 and 25, the program prints `"Your BMI is 22, you have a normal weight."`
> - If the BMI is between 25 and 30, the program prints `"Your BMI is 28, you are slightly overweight."`
> - If the BMI is between 30 and 35, the program prints `"Your BMI is 33, you are obese."`
> - If the BMI is greater than 35, the program prints `"Your BMI is 36, you are clinically obese."`

{:.prompt-tip}

> **Note**: The BMI is rounded to the nearest whole number using the `round()` function.

```python
height = float(input("Enter your height in m: "))
weight = float(input("Enter your weight in kg: "))
bmi = round(weight / height ** 2)

if bmi < 18.5:
    print(f"Your BMI is {bmi}, you are underweight.")
elif bmi < 25:
    print(f"Your BMI is {bmi}, you have a normal weight.")
elif bmi < 30:
    print(f"Your BMI is {bmi}, you are slightly overweight.")
elif bmi < 35:
    print(f"Your BMI is {bmi}, you are obese.")
else:
    print(f"Your BMI is {bmi}, you are clinically obese.")
```

## Leap Year

{:.prompt-info}

> This program checks if a year is a leap year.
>
> - A leap year is a year that is divisible by 4, except for years that are divisible by 100.
> - Years that are divisible by 400 are also leap years.
> - For example, the year 2000 is a leap year, but the year 2100 will not be a leap year.

```python
year = int(input("Which year do you want to check? "))

if year % 4 == 0:
    if year % 100 == 0:
        if year % 400 == 0:
            print("Leap year.")
        else:
            print("Not leap year.")
    else:
        print("Leap year.")
else:
    print("Not leap year.")
```

## Multiple If Statements

{:.prompt-info}

> This program checks if a number is odd or even.
>
> - The program asks the user for a number.
> - The program then checks if the number is odd or even.
> - The program prints a message based on the result.

```python
number = int(input("Which number do you want to check? "))
if number % 2 == 0:
    print("This is an even number.")
else:
    print("This is an odd number.")
```

### Pizza Order

- {:.prompt-info}

> This program calculates the cost of a pizza order.
>
> - The program asks the user for the size of the pizza they want to order. It then asks the user:
> - for the type of pizza they want to order.
> - if they want pepperoni on their pizza or extra cheese.
> - Finally it calculates the total cost of the pizza order.

{:.prompt-tip}

> **Note**: The program uses nested `if` statements to calculate the total cost of the pizza order.

```python
print("Welcome to Python Pizza Deliveries!")
size = input("What size pizza do you want? S, M, or L ")
add_pepperoni = input("Do you want pepperoni? Y or N ")
extra_cheese = input("Do you want extra cheese? Y or N ")

bill = 0

if size == "S":
    bill += 15
elif size == "M":
    bill += 20
else:
    bill += 25

if add_pepperoni == "Y":
    if size == "S":
        bill += 2
    else:
        bill += 3

if extra_cheese == "Y":
    bill += 1

print(f"Your final bill is: ${bill}.")
```

## Logical Operators

Logical operators are used to combine conditional statements.
In python, there are three logical operators:

- `and` - Returns `True` if both statements are `True`
- `or` - Returns `True` if one of the statements is `True`
- `not` - Reverse the result, returns `False` if the result is `True`

### Example

```python
x = 5
y = 10

if x > y and x > 0:
    print("x is greater than y and x is greater than 0")
elif x < y or x < 0:
    print("x is less than y or x is less than 0")
else:
    print("x is equal to y")
```

### Love Calculator

The Love Calculator is a program that calculates the compatibility between two people.

- The user enters their name and their partner's name.
- The program then calculates the love score.

{:.prompt-info}

> To work out the love score between two people:
>
> - Take both people's names and check for the number of times the letters in the word TRUE occurs.
> - Then check for the number of times the letters in the word LOVE occurs.
> - Then combine these numbers to make a 2 digit number.
> - For Love Scores **less than 10** or **greater than 90**, the message should be:
> - `"Your score is **x**, you go together like coke and mentos."`
> - For Love Scores **between 40** and **50**, the message should be:
> - `"Your score is **y**, you are alright together."`
> - Otherwise, the message will just be their score. e.g.:
> - `"Your score is **z**."`

```python
print("Welcome to the Love Calculator!")
name1 = input("What is your name? \n")
name2 = input("What is their name? \n")

combined_string = name1 + name2
lower_case_string = combined_string.lower()

t = lower_case_string.count("t")
r = lower_case_string.count("r")
u = lower_case_string.count("u")
e = lower_case_string.count("e")

true = t + r + u + e

l = lower_case_string.count("l")
o = lower_case_string.count("o")
v = lower_case_string.count("v")
e = lower_case_string.count("e")

love = l + o + v + e

love_score = int(str(true) + str(love))

if (love_score < 10) or (love_score > 90):
    print(f"Your love score is {love_score}, you go together like coke and mentos.")
elif (love_score >= 40) and (love_score <= 50):
    print(f"Your score is {love_score}, you are alright together.")
else:
    print(f"Your score is {love_score}.")
```

### Treasure Island

{:.prompt-info}

> This program is a game called Treasure Island.
>
> - The program prints a welcome message for the user.
> - The program then asks the user to make a choice.
> - The program prints a message based on the user's choice.
> - The program then asks the user to make another choice.
> - The program prints a message based on the user's choice.

{:.prompt-tip}

> **Note**: The program uses nested `if` statements to print different messages based on the user's choice.

```python
print('''
*******************************************************************************
          |                   |                  |                     |
 _________|________________.=""_;=.______________|_____________________|_______
|                   |  ,-"_,=""     `"=.|                  |
|___________________|__"=._o`"-._        `"=.______________|___________________
          |                `"=._o`"=._      _`"=._                     |
 _________|_____________________:=._o "=._."_.-="'"=.__________________|_______
|                   |    __.--" , ; `"=._o." ,-"""-._ ".   |
|___________________|_._"  ,. .` ` `` ,  `"-._"-._   ". '__|___________________
          |           |o`"=._` , "` `; .". ,  "-._"-._; ;              |
 _________|___________| ;`-.o`"=._; ." ` '`."\` . "-._ /_______________|_______
|                   | |o;    `"-.o`"=._``  '` " ,__.--o;   |
|___________________|_| ;     (#) `-.o `"=.`_.--"_o.-; ;___|___________________
____/______/______/___|o;._    "      `".o|o_.--"    ;o;____/______/______/____
/______/______/______/_"=._o--._        ; | ;        ; ;/______/______/______/_
____/______/______/______/__"=._o--._   ;o|o;     _._;o;____/______/______/____
/______/______/______/______/____"=._o._; | ;_.--"o.--"_/______/______/______/_
____/______/______/______/______/_____"=.o|o_.--""___/______/______/______/____
/______/______/______/______/______/______/______/______/______/______/_____ /
*******************************************************************************
''')

print("Welcome to Treasure Island.")
print("Your mission is to find the treasure.")

choice1 = input(
    'You\'re at a crossroad, where do you want to go? Type "left" or "right".\n'
).lower()

if choice1 == "left":
    choice2 = input(
        'You\'ve come to a lake. There is an island in the middle of the lake. Type "wait" to wait for a boat. Type "swim" to swim across.\n'
    ).lower()
    if choice2 == "wait":
        choice3 = input(
            "You arrive at the island unharmed. There is a house with 3 doors. One red, one yellow and one blue. Which colour do you choose?\n"
        ).lower()
        if choice3 == "red":
            print("It's a room full of fire. Game Over.")
        elif choice3 == "yellow":
            print("You found the treasure! You Win!")
        elif choice3 == "blue":
            print("You enter a room of beasts. Game Over.")
        else:
            print("You chose a door that doesn't exist. Game Over.")
    else:
        print("You get attacked by an angry trout. Game Over.")
else:
    print("You fell into a hole. Game Over.")
```
