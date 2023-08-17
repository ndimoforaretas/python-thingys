---
layout: post
title: 100 Days Of Python - Day 4
date: 2023-08-17 04:31 +0000
categories: [Python Tutorial, Day 4]
tags:
  [
    modules,
    random,
    data structures,
    list,
    nested list,
    index error,
    treasure map,
    banker roulette,
    rock paper scissors,
  ]
---

## Day 4

- <a href="https://docs.python.org/3.11/tutorial/datastructures.html" target="_blank">Data Structures</a> on Python Documentation

## Module

A module is a file containing Python definitions and statements. The file name is the module name with the suffix `.py` appended.

## Importing Modules

We can import modules in Python using the `import` keyword.

```python
import math
```

We can also import specific functions from a module.

```python
from math import sqrt
```

## Random Module

The `random` module provides access to functions that support many operations. Perhaps the most important thing is that it allows you to generate random numbers.

```python
import random

random_integer = random.randint(1, 10)# generates a random integer between 1 and 10
print(random_integer)
```

### Heads or Tails

We can use the `random` module to simulate a coin toss.
This program will print either `Heads` or `Tails` randomly.

```python
import random

random_integer = random.randint(0, 1)

if random_integer == 0:
    print("Heads")
else:
    print("Tails")
```

## Data Structures

- These are different ways of organizing and storing data in our computer's memory so that we can use it efficiently.
- The data in a data structure have a relationship with each other (something in common).
- Data structures are used to organize data in a particular order.
- There are four built-in data structures in Python:
  - List
  - Dictionary
  - Tuple
  - Set

### List

- similar to arrays in other programming languages
- can store multiple pieces of data in one place

```python

fruits = ["Apple", "Peach", "Pear"] # list of strings
print(fruits[0]) # prints "Apple"

```

### List Operations

{:.prompt-danger}

> The operators do not need to be memorized. You can always look them up in the <a href="https://docs.python.org/3.11/tutorial/datastructures.html" target="_blank">Python Documentation</a>.

Below are some of the operations that can be performed on lists:

- `append()` - adds an item to the end of the list
- `extend()` - adds all elements of one list to another
- `insert()` - inserts an item at a given position
- `remove()` - removes an item from a list
- `pop()` - removes and returns an element at a given position
- `clear()` - removes all items from a list
- `index()` - returns the index of an element in a list
- `count()` - returns the number of elements with the specified value
- `sort()` - sorts the list
- `reverse()` - reverses the order of the list
- `copy()` - returns a copy of the list
- `len()` - returns the length of the list
- `max()` - returns the maximum value in the list
- `min()` - returns the minimum value in the list

```python
fruits = ["Apple", "Peach", "Pear"]
fruits.append("Banana") # adds "Banana" to the end of the list
print(fruits) # prints ["Apple", "Peach", "Pear", "Banana"]

fruits.extend(["Mango", "Grapes"]) # adds all elements of the list to the end of the list
print(fruits) # prints ["Apple", "Peach", "Pear", "Banana", "Mango", "Grapes"]

fruits.insert(0, "Orange") # inserts "Orange" at index 0
print(fruits) # prints ["Orange", "Apple", "Peach", "Pear", "Banana", "Mango", "Grapes"]

fruits.remove("Banana") # removes "Banana" from the list
print(fruits) # prints ["Orange", "Apple", "Peach", "Pear", "Mango", "Grapes"]

fruits.pop(0) # removes and returns the element at index 0
print(fruits) # prints ["Apple", "Peach", "Pear", "Mango", "Grapes"]

fruits.clear() # removes all elements from the list
print(fruits) # prints []

fruits = ["Apple", "Peach", "Pear"]
print(fruits.index("Pear")) # prints 2

print(fruits.count("Apple")) # prints 1

fruits.sort() # sorts the list
print(fruits) # prints ["Apple", "Peach", "Pear"]

fruits.reverse() # reverses the order of the list
print(fruits) # prints ["Pear", "Peach", "Apple"]

fruits_copy = fruits.copy() # returns a copy of the list
print(fruits_copy) # prints ["Pear", "Peach", "Apple"]

print(len(fruits)) # prints 3

print(max(fruits)) # prints Pear

print(min(fruits)) # prints Apple
```

### Banker Roulette

This program will select a random name from a list of names.

```python
import random

names_string = input("Give me everybody's names, separated by a comma. ")
names = names_string.split(", ")

random_name = random.choice(names)

print(f"{random_name} is going to buy the meal today!")
```

- Another way to select a random name from a list of names is to use the `randint()` function.

```python

import random

names_string = input("Give me everybody's names, separated by a comma. ")
names = names_string.split(", ")

number_of_names = len(names)
random_index = random.randint(0, number_of_names - 1)

random_name = names[random_index]

print(f"{random_name} is going to buy the meal today!")
```

### Index Errors and Working with Nested Lists

1. **Index Errors**

{:.prompt-danger}

> - An `IndexError` occurs when you try to access an index that does not exist. For example, if you have a list with 3 elements, the only valid indices are 0, 1, and 2. If you try to access index 3, you will get an `IndexError`.

```python
fruits = ["Apple", "Peach", "Pear"]
print(fruits[3]) # IndexError: list index out of range
```

{:.prompt-tip}

> - To avoid `IndexError`, you can use the `len()` function to get the number of elements in a list, and then subtract 1 from it to get the last index.

```python
fruits = ["Apple", "Peach", "Pear"]
number_of_fruits = len(fruits)
print(fruits[number_of_fruits - 1]) # prints Pear
```

2. **Nested Lists**

- Nested lists are lists that contain other lists.
- It helps us to keep track of related data without changing their order.

```python
fruits = ["Strawberries", "Nectarines", "Apples", "Grapes", "Peaches", "Cherries", "Pears"]
vegetables = ["Spinach", "Kale", "Tomatoes", "Celery", "Potatoes"]

dirty_dozen = [fruits, vegetables]

print(dirty_dozen) # prints [["Strawberries", "Nectarines", "Apples", "Grapes", "Peaches", "Cherries", "Pears"], ["Spinach", "Kale", "Tomatoes", "Celery", "Potatoes"]]
```

### Treasure Map

This program will create a map using nested lists.

```python
row1 = ["⬜️", "⬜️", "⬜️"]
row2 = ["⬜️", "⬜️", "⬜️"]
row3 = ["⬜️", "⬜️", "⬜️"]

map = [row1, row2, row3]

print(f"{row1}\n{row2}\n{row3}") # prints ["⬜️", "⬜️", "⬜️"] ["⬜️", "⬜️", "⬜️"] ["⬜️", "⬜️", "⬜️"]

position = input("Where do you want to put the treasure? ")

horizontal = int(position[0])
vertical = int(position[1])

map[vertical - 1][horizontal - 1] = "X"

print(f"{row1}\n{row2}\n{row3}") # prints ["⬜️", "⬜️", "⬜️"] ["⬜️", "X", "⬜️"] ["⬜️", "⬜️", "⬜️"]
```

## Rock Paper Scissors

This program will simulate a game of rock paper scissors.

```python
import random

rock = '''
    _______
---'   ____)
      (_____)
      (_____)
      (____)
---.__(___)
'''

paper = '''
    _______
---'   ____)____
          ______)
          _______)
         _______)
---.__________)
'''

scissors = '''
    _______
---'   ____)____
          ______)
       __________)
      (____)
---.__(___)
'''

game_images = [rock, paper, scissors]

user_choice = int(input("What do you choose? Type 0 for Rock, 1 for Paper or 2 for Scissors.\n"))
print(game_images[user_choice])

computer_choice = random.randint(0, 2)
print("Computer chose:")
print(game_images[computer_choice])

if user_choice >= 3 or user_choice < 0:
    print("You typed an invalid number, you lose!")
elif user_choice == 0 and computer_choice == 2:
    print("You win!")
elif computer_choice == 0 and user_choice == 2:
    print("You lose")
elif computer_choice > user_choice:
    print("You lose")
elif user_choice > computer_choice:
    print("You win!")
elif computer_choice == user_choice:
    print("It's a draw")
```
