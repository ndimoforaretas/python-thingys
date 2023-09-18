---
layout: post
title: 100 Days Of Python - Day 30
date: 2023-09-10 08:10 +0000
categories: [Python Tutorial, Day 30]
tags: [day 30, handling errors and exceptions, json data]
---

## Day 30

## Handling Errors and Exceptions

### Errors

- `Errors` are mistakes that occur during the execution of a program.
- `Errors` are caused by invalid code.
- Some common errors in Python include:
  - `KeyError` - This error occurs when a dictionary does not have a specific key.
  - `IndexError` - This error occurs when you try to access an index in a list that does not exist.
  - `NameError` - This error occurs when a variable is not defined.
  - `TypeError` - This error occurs when an operation or function is applied to the wrong type.
  - `ValueError` - This error occurs when a built-in operation or function receives an argument that has the right type but an inappropriate value.

### Exceptions

- `Exceptions` are errors that occur during the execution of a program.
- They are `handled` using `try` and `except` , `else` and `finally` statements.
- `Exceptions` are raised when the program encounters an error.

#### Try, Except, Else, and Finally

- `try` - `except` - `else` - `finally` statements are used to `handle` `exceptions`.
- `try` is used to `test` a block of code for errors and is used when we expect an error to occur.
- `except` is used to `handle` the `exception`. That is, if the try code does not work, the code in the except block will be executed.
  - `except` can be used to handle a specific error.
  - It can also be used to handle multiple errors.
  - It can be used to catch the error and print a message.
- `else` is used to execute code if the try code does not raise an exception.
- `finally` is used to execute code, regardless of whether the try code raises an exception or not.

### Example

```python
try:
    file = open("a_file.txt") # FileNotFoundError
    a_dictionary = {"key": "value"}
    print(a_dictionary["key"]) # KeyError
except FileNotFoundError:
    file = open("a_file.txt", "w") # Create a file
    file.write("Something")
except KeyError as error_message: # Catch the error and print a message
    print(f"The key {error_message} does not exist.") # The key 'key' does not exist.
else:
    content = file.read()
    print(content)
finally:
    file.close() # File was closed.
    print("File was closed.")# File was closed.
```

### Raising Exceptions

- `raise` is used to raise an exception.
- `raise` can be used to raise a specific error with a `type` and a `message`.
- `raise` can be used in situations where we want to raise an error if a certain condition is met. For example, if we want to raise an error if a number is negative.

### Example

```python
height = float(input("Height: "))
weight = int(input("Weight: "))
if height > 3:
    raise ValueError("Human height should not be over 3 meters.")
bmi = weight / height ** 2
print(bmi)
```

- In the above example,
  - if the height is greater than 3,
  - a `ValueError` will be raised with the message `Human height should not be over 3 meters.`

### IndexError Handling

- `IndexError` occurs when you try to access an index in a list that does not exist.
- `IndexError` can be handled using `try` and `except` statements.

### Example

```python
fruits = ["Apple", "Pear", "Orange"]
# IndexError: list index out of range
# print(fruits[3])
# Handle IndexError
try:
    print(fruits[3])
except IndexError:
    print("Index does not exist.")
```

- In the above example,
  - if the index does not exist,
  - the `IndexError` will be handled and the message `Index does not exist.` will be printed.

### KeyError Handling

- `KeyError` occurs when a dictionary does not have a specific key.

### Example

```python
facebook_posts = [
    {"Likes": 21, "Comments": 2},
    {"Likes": 13, "Comments": 2, "Shares": 1},
    {"Likes": 33, "Comments": 8, "Shares": 3},
    {"Comments": 4, "Shares": 2},
    {"Comments": 1, "Shares": 1},
    {"Likes": 19, "Comments": 3},
]
total_likes = 0

# KeyError: 'Likes'
# for post in facebook_posts:
#     total_likes = total_likes + post["Likes"]
# print(total_likes)

# Handle KeyError
for post in facebook_posts:
    try:
        total_likes = total_likes + post["Likes"]
    except KeyError:
        pass
print(total_likes)
```

- In the abouve example,
  - we are trying to access the key `Likes` in the dictionary `post`.
  - In the first loop, the `KeyError` will be raised because the key `Likes` does not exist in the dictionary `post`.
  - In the second loop, the `KeyError` is handled and the loop will continue.

### TypeError Handling

- `TypeError` occurs when an operation or function is applied to the wrong type.

{: .prompt-tip}

> - The following example is based on the NATO Phonetic Alphabet project from Day 26.
> - If the user enters a name that contains a `number`, the `TypeError` will be raised.
>   In order to handle the `TypeError`, we can use `try` and `except` statements.

### Example

```python
import pandas

data = pandas.read_csv("nato_phonetic_alphabet.csv")

phonetic_dict = {row.letter: row.code for (index, row) in data.iterrows()}

# TypeError: 'int' object is not iterable
# name = input("Enter a name: ").upper()
# nato_list = [phonetic_dict[letter] for letter in name]
# print(nato_list)

# Handle TypeError
try:
    name = input("Enter a name: ").upper()
    nato_list = [phonetic_dict[letter] for letter in name]
except KeyError:
    print("Sorry, only letters in the alphabet please.")
    generate_phonetic()
else:
    print(nato_list)

generate_phonetic()

# Output
# Enter a name: 123
# Sorry, only letters in the alphabet please.
```

## JSON Data

- `JSON` stands for `JavaScript Object Notation`.

### Writing JSON Data

- `JSON` data can be written to a file using the `json` module which is built into Python.
- The `json` module has the following methods:
  - `dump()` - Used to write data to a file.
  - `dumps()` - Used to convert a Python object into a `JSON` string.
- The `dump()` method takes two arguments:
  - The data to be written.
  - The file to write the data to.
  - and optionally, the `indent` argument which is used to format the `JSON` data.

### Example

```python
import json

# Create a dictionary
data = {
    "name": "John",
    "age": 30,
    "married": True,
    "divorced": False,
    "children": ("Ann", "Billy"),
    "pets": None,
    "cars": [
        {"model": "BMW 230", "mpg": 27.5},
        {"model": "Ford Edge", "mpg": 24.1},
    ],
}

# Convert the dictionary to a JSON string
json_data = json.dumps(data)

# Write the JSON data to a file
with open("data.json", "w") as file:
    json.dump(json_data, file, indent=4)

# Output
# {
#     "name": "John",
#     "age": 30,
#     "married": true,
#     "divorced": false,
#     "children": [
#         "Ann",
#         "Billy"
#     ],
#     "pets": null,
#     "cars": [
#         {
#             "model": "BMW 230",
#             "mpg": 27.5
#         },
#         {
#             "model": "Ford Edge",
#             "mpg": 24.1
#         }
#     ]
# }
```

### Reading JSON Data

- `JSON` data can be read from a file also using the `json` module which is built into Python.
- The `json` module has the following methods:
  - `load()` - Used to read data from a file.
  - `loads()` - Used to convert a `JSON` string into a Python object.
- The `load()` method takes one argument:
  - The file to read the data from.
- It converts the `JSON` data into a Python dictionary.

### Example

```python
import json

# Read the JSON data from a file
with open("data.json", "r") as file:
    json_data = json.load(file)

# Convert the JSON data into a Python dictionary
data = json.loads(json_data)

print(data["name"]) # John
```

### Updating JSON Data

- `JSON` data can be updated using the `json` module which is built into Python.
- The `json` module has the following methods:
  - `load()` - Used to read data from a file.
  - `loads()` - Used to convert a `JSON` string into a Python object.
  - `dump()` - Used to write data to a file.
  - `dumps()` - Used to convert a Python object into a `JSON` string.
- Update the `JSON` data as follows:
  - Read the `JSON` data from the file.
  - Convert the `JSON` data into a Python dictionary.
  - Update the Python dictionary.
  - Convert the Python dictionary into `JSON` data.
  - Write the `JSON` data to the file.

### Example

```python
import json

# Read the JSON data from a file
with open("data.json", "r") as file:
    json_data = json.load(file)

# Convert the JSON data into a Python dictionary
data = json.loads(json_data)

# Update the Python dictionary
data["age"] = 31

# Convert the Python dictionary into JSON data
json_data = json.dumps(data)

# Write the JSON data to a file
with open("data.json", "w") as file:
    json.dump(json_data, file, indent=4)

# Output
# {
#     "name": "John",
#     "age": 31,
#     "married": true,
#     "divorced": false,
#     "children": [
#         "Ann",
#         "Billy"
#     ],
#     "pets": null,
#     "cars": [
#         {
#             "model": "BMW 230",
#             "mpg": 27.5
#         },
#         {
#             "model": "Ford Edge",
#             "mpg": 24.1
#         }
#     ]
# }
```
