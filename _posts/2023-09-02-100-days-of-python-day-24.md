---
layout: post
title: 100 Days Of Python - Day 24
date: 2023-09-02 15:00 +0000
categories: [Python Tutorial, Day 24]
tags: [day 24, mail merge, file, read, write, append]
---

## Day 24

### How to use python to read and write files

In python, we can use the `open()` function to open a file.

- The `open()` function takes two arguments:
  - the name of the file and
  - the mode in which we want to open the file.
- The mode can be either `r` for read, `w` for write, `a` for append, or `r+` for read and write.
- If we don't specify the mode, the default mode is `r`.
- if the file doesn't exist, the `open()` function with the write `w` mode activated for example will create a new file.

```python
# main.py
# open a file in read mode
with open("my_file.txt") as file:
    contents = file.read()
    print(contents)
```

```python
# main.py
# open a file in write mode
# write mode will overwrite the existing text in the file
with open("my_file.txt", mode="w") as file:
    file.write("New text.")
```

```python
# main.py
# open a file in append mode
# append mode will append the new text to the end of the file
with open("my_file.txt", mode="a") as file:
    file.write("\nNew text.")
```

```python
# main.py
# open a file in read and write mode
# read and write mode will overwrite the existing text in the file
with open("my_file.txt", mode="r+") as file:
    file.write("\nNew text.")
    file.seek(0)
    contents = file.read()
    print(contents)
```

- It is advisable to use the `with` keyword when working with files.
- The `with` keyword will automatically close the file after the indented block of code.

```python
# main.py
# open a file in read mode
with open("my_file.txt") as file:
    contents = file.read()
    print(contents)
```

- If we don't use the `with` keyword, we have to close the file manually using the `close()` method.

```python
# main.py
# open a file in read mode
file = open("my_file.txt")
contents = file.read()
print(contents)
file.close()
```

### The mail merge project

- In this project, we will create a letter for each name in the `names.txt` file.
- The letter will be created using the `starting_letter.txt` file.
- The `names.txt` file contains the names of the people we want to send the letter to.
- The `starting_letter.txt` file contains the letter template.
- The letter template contains the placeholder `[name]` which will be replaced with the name of the person we want to send the letter to.
- The letter template also contains the placeholder `[date]` which will be replaced with the current date.
- The letter template also contains the placeholder `[letter]` which will be replaced with the content of the letter.

```python
# main.py
# create a letter for each name in the names.txt file
# the letter will be created using the starting_letter.txt file
# the names.txt file contains the names of the people we want to send the letter to
# the starting_letter.txt file contains the letter template
# the letter template contains the placeholder [name] which will be replaced with the name of the person we want to send the letter to
# the letter template also contains the placeholder [date] which will be replaced with the current date
# the letter template also contains the placeholder [letter] which will be replaced with the content of the letter
# open the names.txt file in read mode
with open("Input/Names/invited_names.txt") as names_file:
    # read the content of the names.txt file
    names = names_file.readlines()

# open the starting_letter.txt file in read mode

with open("Input/Letters/starting_letter.txt") as letter_file:
    # read the content of the starting_letter.txt file
    letter_contents = letter_file.read()

    # loop through the names
    for name in names:
        # remove the newline character from the name
        stripped_name = name.strip()

        # replace the placeholder [name] with the name of the person we want to send the letter to
        new_letter = letter_contents.replace("[name]", stripped_name)

        # create a new file for each name
        with open(f"Output/ReadyToSend/letter_for_{stripped_name}.txt", mode="w") as completed_letter:
            # write the content of the new letter to the new file
            completed_letter.write(new_letter)
```
