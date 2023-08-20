---
layout: post
title: 100 Days Of Python - Day 8
date: 2023-08-19 20:21 +0000
categories: [Python Tutorial, Day 8]
tags:
  [
    day 8,
    functions,
    keyword arguments,
    paint area calculator,
    prime number checker,
    caesar cipher,
  ]
---

## Day 8

### Keyword Arguments

You can pass arguments to a function by using the `=` sign.

```python
def greet(name, location):
    print(f"Hello {name}")
    print(f"What is it like in {location}?")

greet(location="London", name="Jack")

# Output:
# Hello Jack
# What is it like in London?

```

- keyword arguments must always follow positional arguments.

### Paint Area Calculator

```python
import math

def paint_calc(height, width, cover):
    number_of_cans = math.ceil((height * width) / cover)
    print(f"You'll need {number_of_cans} cans of paint.")

test_h = int(input("Height of wall: "))
test_w = int(input("Width of wall: "))
coverage = 5
paint_calc(height=test_h, width=test_w, cover=coverage)

# Output:
# Height of wall: 3
# Width of wall: 9
# You'll need 6 cans of paint.

```

### Prime Number Checker

- Prime numbers are numbers that can only be cleanly divided by itself and 1.

```python
def prime_checker(number):
        is_prime = True
    for i in range(2, number):
        if number % i == 0:
            is_prime = False
    if is_prime:
        print("It's a prime number.")
    else:
        print("It's not a prime number.")

    n = int(input("Check this number: "))
    prime_checker(number=n)

# Output:
# Check this number: 7
# It's a prime number.

```

### Caesar Cipher

- The Caesar Cipher is a simple encryption technique that shifts each letter by a set number of places.

```python
def caesar(start_text, shift_amount, cipher_direction):
    end_text = ""
    if cipher_direction == "decode":
        shift_amount *= -1
    for char in start_text:
        if char in alphabet:
            position = alphabet.index(char)
            new_position = position + shift_amount
            end_text += alphabet[new_position]
        else:
            end_text += char
    print(f"Here's the {cipher_direction}d result: {end_text}")

from art import logo
print(logo)

alphabet = [
    "a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"
]

should_continue = True

while should_continue:
    direction = input("Type 'encode' to encrypt, type 'decode' to decrypt:\n")
    text = input("Type your message:\n").lower()
    shift = int(input("Type the shift number:\n"))
    shift = shift % 26
    caesar(start_text=text, shift_amount=shift, cipher_direction=direction)
    result = input("Type 'yes' if you want to go again. Otherwise type 'no'.\n")
    if result == "no":
        should_continue = False
        print("Goodbye")

# Output:
#
#   _   __  __ _  __ _  ___   ___   ___   ___   ___   ___
#  | | |  \/  | |/ /| |/ /  / _ \ / _ \ / _ \ / _ \ / _ \
#  | |_| |\/| | ' / | ' /  |  __/| (_) | (_) | (_) |  __/
#   \__,_|  |_|_|\_\|_|\_\  \___| \___/ \___/ \___/ \___|
#
#
# Type 'encode' to encrypt, type 'decode' to decrypt:
# encode
# Type your message:
# hello
# Type the shift number:
# 5
# Here's the encoded result: mjqqt
# Type 'yes' if you want to go again. Otherwise type 'no'.
# yes
# Type 'encode' to encrypt, type 'decode' to decrypt:
# decode
# Type your message:
# mjqqt
# Type the shift number:
# 5
# Here's the decoded result: hello
# Type 'yes' if you want to go again. Otherwise type 'no'.
# no
# Goodbye

```
