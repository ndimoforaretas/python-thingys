---
layout: post
title: 100 Days Of Python - Day 12
date: 2023-08-20 10:30 +0000
categories: [Python Tutorial, Day 12]
tags: [scope, namespace, global constants, the number guessing game, day 12]
---

## Day 12

## Scope

- Scope refers to the visibility of variables.
- Variables defined `outside` of a function `are accessible inside` the function.
- Variables defined `inside` a function are `not accessible outside` the function.

```python
enemies = 1

def increase_enemies():
    enemies = 2
    print(f"enemies inside function: {enemies}")

increase_enemies()
print(f"enemies outside function: {enemies}")

# Output:
# enemies inside function: 2
# enemies outside function: 1
```

### Local Scope

- Variables defined in functions are only accessible in the function.
- Variables defined in functions are called `local variables`.

```python
def drink_potion():
    potion_strength = 2
    print(potion_strength)

drink_potion()
print(potion_strength)

# Output:
# 2
# NameError: name 'potion_strength' is not defined
```

### Global Scope

- Variables defined outside of functions are called `global variables`.
- Global variables are accessible inside functions.

```python
player_health = 10

def drink_potion():
    potion_strength = 2
    print(player_health)

drink_potion()
print(player_health)

# Output:
# 10
# 10
```

### Namespace

- A `namespace` is a collection of names.
- Each namespace has its own `scope`.
- There can be `local`, `global`, and `built-in` namespaces.
- The `built-in` namespace contains functions like `print()`, `input()`, `len()`, etc.
- The `global` namespace contains variables defined outside of functions.
- The `local` namespace contains variables defined inside functions.
- The `local` namespace is created when a function is called, and is destroyed when the function returns.
- The `global` namespace is created when the program starts, and is destroyed when the program ends.
- The `built-in` namespace is created when the program starts, and is destroyed when the program ends.
- The `local` namespace can access the `global` and `built-in` namespaces.
- The `global` namespace can access the `built-in` namespace.
- The `built-in` namespace cannot access the `global` or `local` namespaces.

### There is no Block Scope

- In some programming languages, variables defined inside `if` statements are not accessible outside of the `if` statement.
- This is called `block scope`.
- Python does not have `block scope`.
- Variables defined inside `if` statements are accessible outside of the `if` statement.

```python
game_level = 3
enemies = ["Skeleton", "Zombie", "Alien"]

if game_level < 5:
    new_enemy = enemies[0]

print(new_enemy)

# Output:
# Skeleton
```

### Modifying Global Scope

- If you want to modify a global variable inside a function, use the `global` keyword.

```python
enemies = 1

def increase_enemies():
    global enemies
    enemies = 2
    print(f"enemies inside function: {enemies}")

increase_enemies()
print(f"enemies outside function: {enemies}")

# Output:
# enemies inside function: 2
# enemies outside function: 2
```

- If you want to modify a global variable inside a function, use the `global` keyword.

```python
enemies = 1

def increase_enemies():
    global enemies
    enemies = 2
    print(f"enemies inside function: {enemies}")

increase_enemies()
print(f"enemies outside function: {enemies}")

# Output:
# enemies inside function: 2
# enemies outside function: 2
```

### Global Constants

- Global constants are variables that are accessible everywhere, but cannot be modified.
- Global constants are usually written in `ALL_CAPS`.

```python
PI = 3.14159
URL = "https://www.google.com"
TWITTER_HANDLE = "@jack"
```

### The Number Guessing Game

{: .prompt-info}

> #### Instructions:
>
> - You are going to build a **higher or lower** game.
>
> The game works like this:
>
> - The computer randomly chooses a number between 0 and 100.
> - The user is then asked to **guess** a number.
> - If the user's guess is **higher** than the computer's number, then the user is told to **go lower**.
> - If the user's guess is **lower** than the computer's number, then the user is told to **go higher**.
> - Then the user is asked to guess again.
> - This process repeats until the user guesses the computer's number.
> - Once the user guesses the computer's number, the game restarts.
> - **Important** Print **"It's higher"** or **"It's lower"** to give the user a hint. If they guess the number correctly, tell them they got it right, and the game is over.
> - **Hint**: you can generate a random number between 0 and 100 using:
>   ```python
>   import random
>   print(random.randint(0, 100))
>   ```

```python
import random

EASY_LEVEL_TURNS = 10
HARD_LEVEL_TURNS = 5

def set_difficulty():
    level = input("Choose a difficulty. Type 'easy' or 'hard': ")
    if level == "easy":
        return EASY_LEVEL_TURNS
    else:
        return HARD_LEVEL_TURNS

def check_answer(guess, answer, turns):
    """Checks answer against guess. Returns the number of turns remaining."""
    if guess > answer:
        print("Too high.")
        return turns - 1
    elif guess < answer:
        print("Too low.")
        return turns - 1
    else:
        print(f"You got it! The answer was {answer}.")

def game():
    print("Welcome to the Number Guessing Game!")
    print("I'm thinking of a number between 1 and 100.")
    answer = random.randint(1, 100)
    print(f"Pssst, the correct answer is {answer}")

    turns = set_difficulty()
    guess = 0
    while guess != answer:
        print(f"You have {turns} attempts remaining to guess the number.")

        guess = int(input("Make a guess: "))

        turns = check_answer(guess, answer, turns)
        if turns == 0:
            print("You've run out of guesses, you lose.")
            return
        elif guess != answer:
            print("Guess again.")

game()

# Output:
# Welcome to the Number Guessing Game!
# I'm thinking of a number between 1 and 100.
# Pssst, the correct answer is 87
# Choose a difficulty. Type 'easy' or 'hard': hard
# You have 5 attempts remaining to guess the number.
# Make a guess: 50
# Too low.
# Guess again.
# You have 4 attempts remaining to guess the number.
# Make a guess: 75
# Too high.

# ...
```
