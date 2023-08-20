---
layout: post
title: 100 Days Of Python - Day 9
date: 2023-08-20 04:45 +0000
categories: [Python Tutorial, Day 9]
tags: [day 9, dictionaries, grading program, nesting, travel log, blind auction]
---

## Day 9

## Dictionaries

- Dictionaries are unordered collections of data in key-value pairs.
- Dictionaries are defined using curly braces `{}`.
- They are similar to objects in JavaScript.

```python
programming_dictionary = {
    "Bug": "An error in a program that prevents the program from running as expected.",
    "Function": "A piece of code that you can easily call over and over again.",
}

print(programming_dictionary["Bug"])

# Output:
# An error in a program that prevents the program from running as expected.
```

- You can add new items to a dictionary using the key.

```python
programming_dictionary["Loop"] = "The action of doing something over and over again."

print(programming_dictionary)

# Output:
# {
#     "Bug": "An error in a program that prevents the program from running as expected.",
#     "Function": "A piece of code that you can easily call over and over again.",
#     "Loop": "The action of doing something over and over again.",
# }
```

- You can create an empty dictionary.

```python
empty_dictionary = {}

print(empty_dictionary)

# Output:
# {}
```

- You can wipe an existing dictionary.

```python
programming_dictionary = {}

print(programming_dictionary)

# Output:
# {}
```

- You can edit an item in a dictionary.

```python
programming_dictionary["Bug"] = "A moth in your computer."

print(programming_dictionary)

# Output:
# {
#     "Bug": "A moth in your computer.",
#     "Function": "A piece of code that you can easily call over and over again.",
#     "Loop": "The action of doing something over and over again.",
# }
```

- You can loop through a dictionary.

```python
for key in programming_dictionary:
    print(key)
    print(programming_dictionary[key])

# Output:
# Bug
# A moth in your computer.
# Function
# A piece of code that you can easily call over and over again.
# Loop
# The action of doing something over and over again.
```

## Grading Program

- You have access to a database of `student_scores` in the format of a dictionary.
- The **keys** in `student_scores` are the **names** of the students and the **values** are their exam **scores**.
- Write a program that **converts their scores to grades**.
- By the end of your program, you should have a new dictionary called `student_grades` that should contain student **names** for **keys** and their **grades** for **values**.
- The final version of the `student_grades` dictionary will be checked.

```python
student_scores = {
    "Harry": 81,
    "Ron": 78,
    "Hermione": 99,
    "Draco": 74,
    "Neville": 62,
}

student_grades = {}

for student in student_scores:
    score = student_scores[student]
    if score > 90:
        student_grades[student] = "Outstanding"
    elif score > 80:
        student_grades[student] = "Exceeds Expectations"
    elif score > 70:
        student_grades[student] = "Acceptable"
    else:
        student_grades[student] = "Fail"

print(student_grades)

# Output:
# {
#     "Harry": "Exceeds Expectations",
#     "Ron": "Acceptable",
#     "Hermione": "Outstanding",
#     "Draco": "Acceptable",
#     "Neville": "Fail",
# }
```

## Nesting

- You can nest lists in a dictionary, dictionaries in a list, and even dictionaries in a dictionary.

```python
capitals = {
    "France": "Paris",
    "Germany": "Berlin",
}

# Nesting a List in a Dictionary

travel_log = {
    "France": ["Paris", "Lille", "Dijon"],
    "Germany": ["Berlin", "Hamburg", "Stuttgart"],
}

# Nesting a Dictionary in a Dictionary

travel_log = {
    "France": {
        "cities_visited": ["Paris", "Lille", "Dijon"],
        "total_visits": 12,
    },
    "Germany": {
        "cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
        "total_visits": 5,
    },
}
```

- Nesting a Dictionary in a List

```python
travel_log = [
    {
        "country": "France",
        "cities_visited": ["Paris", "Lille", "Dijon"],
        "total_visits": 12,
    },
    {
        "country": "Germany",
        "cities_visited": ["Berlin", "Hamburg", "Stuttgart"],
        "total_visits": 5,
    },
]
```

## Travel Log

{: .prompt-info}

> - You are going to write a program that adds to a `travel_log`.
> - You can see a travel_log which is a **List** that contains 2 **Dictionaries**.
> - Write a function that will work with the following line of code to add the entry for Russia to the `travel_log`.
>
> ```python
> add_new_country("Russia", 2, ["Moscow", "Saint Petersburg"])
> ```
>
> - `You've visited Russia 2 times.`
> - `You've been to Moscow and Saint Petersburg.`
> - **DO NOT** modify the `travel_log` directly. You need to create a function that modifies it.
> - **Hint:** Look at the function call above to see what the name of the function should be.

```python
def add_new_country(country, visits, cities):
    # Do your thing
```

```python
travel_log = [
    {
        "country": "France",
        "visits": 12,
        "cities": ["Paris", "Lille", "Dijon"],
    },
    {
        "country": "Germany",
        "visits": 5,
        "cities": ["Berlin", "Hamburg", "Stuttgart"],
    },
]


def add_new_country(country, visits, cities):
    new_country = {}
    new_country["country"] = country
    new_country["visits"] = visits
    new_country["cities"] = cities
    travel_log.append(new_country)


add_new_country("Russia", 2, ["Moscow", "Saint Petersburg"])

print(travel_log)

# Output:
# [
#     {
#         "country": "France",
#         "visits": 12,
#         "cities": ["Paris", "Lille", "Dijon"],
#     },
#     {
#         "country": "Germany",
#         "visits": 5,
#         "cities": ["Berlin", "Hamburg", "Stuttgart"],
#     },
#     {
#         "country": "Russia",
#         "visits": 2,
#         "cities": ["Moscow", "Saint Petersburg"],
#     },
# ]
```

## Blind Auction

{: .prompt-info}

> - You are going to write a program that automatically bids on behalf of the user, using their email address.
> - The bidding will work like this:
> - The program will print a prompt asking for bids.
> - If the user types in a bid, then the program will print a prompt asking for the next bid.
> - If the user doesn't type in a bid, then the bidding will stop.
> - The dictionary `bids` will keep track of the highest bid.
> - **Hint:** There is a function called `clear()` which can clear the terminal screen.
> - **Hint:** There is a function called `sleep()` in the `time` module that can pause the execution of the program for a given number of seconds.
> - **Example Output:**
> - `What is your name?:`
> - `What's your bid?:`
> - `Are there any other bidders? Type 'yes' or 'no'.`
> - `What is your name?:`
> - `What's your bid?:`
> - `Are there any other bidders? Type 'yes' or 'no'.`
> - `What is your name?:`
> - `What's your bid?:`
> - `Are there any other bidders? Type 'yes' or 'no'.`
> - `...`
> - `Are there any other bidders? Type 'yes' or 'no'.`
> - `Winner is [name] with a bid of $[bid]`

```python
# art.py

logo = """
   ___________
   \         /
    )_______(
    |"""""""|_.-._,.---------.,_.-._
    |       | | |               | | ''-.
    |       |_| |_             _| |_..-'
    |_______| '-' `'---------'` '-'
    )"""""""(
   /_________\\
   `'-------'`
"""

# main.py

from replit import clear # a replit module that clears the terminal screen

print(logo)

bids = {}
bidding_finished = False


def find_highest_bidder(bidding_record):
    highest_bid = 0
    winner = ""
    # bidding_record = {"Angela": 123, "James": 321}
    for bidder in bidding_record:
        bid_amount = bidding_record[bidder]
        if bid_amount > highest_bid:
            highest_bid = bid_amount
            winner = bidder
    print(f"The winner is {winner} with a bid of ${highest_bid}")

while not bidding_finished:
    name = input("What is your name?: ")
    price = int(input("What is your bid?: $"))
    bids[name] = price
    should_continue = input("Are there any other bidders? Type 'yes' or 'no'.\n")
    if should_continue == "no":
        bidding_finished = True
        find_highest_bidder(bids)
    elif should_continue == "yes":
        clear()
```
