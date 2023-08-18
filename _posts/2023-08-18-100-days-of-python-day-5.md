---
layout: post
title: 100 Days Of Python - Day 5
date: 2023-08-18 18:50 +0000
categories: [Python Tutorial, Day 5]
tags:
  [
    for loop,
    range,
    average height,
    highest score,
    adding even numbers,
    fizzbuzz,
    password generator,
  ]
---

## Day 5

## Using the for loop with Python Lists

We can use the `for` loop to iterate over a list.

```python
fruits = ["Apple", "Peach", "Pear"]
for fruit in fruits:
    print(fruit)

# Output:
# Apple
# Peach
# Pear
```

### Average Height

We can use the `for` loop to calculate the average height of a list of heights.

```python
student_heights = input("Input a list of student heights ").split()
for n in range(0, len(student_heights)):
    student_heights[n] = int(student_heights[n])

total_height = 0
for height in student_heights:
    total_height += height

number_of_students = 0
for student in student_heights:
    number_of_students += 1

average_height = round(total_height / number_of_students)
print(average_height)
```

### Highest Score

We can use the `for` loop to find the highest score in a list of scores.

```python
student_scores = input("Input a list of student scores ").split()
for n in range(0, len(student_scores)):
    student_scores[n] = int(student_scores[n])

highest_score = 0
for score in student_scores:
    if score > highest_score:
        highest_score = score

print(f"The highest score in the class is: {highest_score}")
```

## for loops and the range() function

We can use the `for` loop with the `range()` function to iterate over a range of numbers.

```python
for number in range(1, 11):
    print(number)

# Output:
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9
# 10
```

### Adding Even Numbers

We can use the `for` loop with the `range()` function to add all the even numbers from 1 to 100.

```python
total = 0
for number in range(2, 101, 2):
    total += number

print(total)
```

### FizzBuzz

We can use the `for` loop with the `range()` function to print the numbers from 1 to 100. If the number is divisible by 3, we print "Fizz". If the number is divisible by 5, we print "Buzz". If the number is divisible by both 3 and 5, we print "FizzBuzz".

```python
for number in range(1, 101):
    if number % 3 == 0 and number % 5 == 0:
        print("FizzBuzz")
    elif number % 3 == 0:
        print("Fizz")
    elif number % 5 == 0:
        print("Buzz")
    else:
        print(number)
```

### Password Generator Project

We can use the `for` loop with the `range()` function to generate a password.

```python
import random

letters = [
    "a",
    "b",
    "c",
    "d",
    "e",
    "f",
    "g",
    "h",
    "i",
    "j",
    "k",
    "l",
    "m",
    "n",
    "o",
    "p",
    "q",
    "r",
    "s",
    "t",
    "u",
    "v",
    "w",
    "x",
    "y",
    "z",
    "A",
    "B",
    "C",
    "D",
    "E",
    "F",
    "G",
    "H",
    "I",
    "J",
    "K",
    "L",
    "M",
    "N",
    "O",
    "P",
    "Q",
    "R",
    "S",
    "T",
    "U",
    "V",
    "W",
    "X",
    "Y",
    "Z",
]

numbers = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]

symbols = ["!", "#", "$", "%", "&", "(", ")", "*", "+"]
print("Welcome to the PyPassword Generator!")
nr_letters = int(input("How many letters would you like in your password?\n"))
nr_symbols = int(input(f"How many symbols would you like?\n"))
nr_numbers = int(input(f"How many numbers would you like?\n"))

password_list = []

for char in range(1, nr_letters + 1):
    password_list.append(random.choice(letters))

for char in range(1, nr_symbols + 1):
    password_list += random.choice(symbols)

for char in range(1, nr_numbers + 1):
    password_list += random.choice(numbers)

random.shuffle(password_list)

password = ""
for char in password_list:
    password += char

print(f"Your password is: {password}")
```
