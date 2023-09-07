---
layout: post
title: 100 Days Of Python - Day 26
date: 2023-09-06 19:20 +0000
categories: [Python Tutorial, Day 26]
tags: [day 26]
---

## Day 26

## List Comprehension

List comprehension is a way to create a new list from an existing list.

- We can use list comprehension to create a new list from an existing list by applying a function to each item in the existing list.

```python
# main.py
# create a new list from an existing list by applying a function to each item in the existing list
numbers = [1, 2, 3]
new_numbers = [n + 1 for n in numbers]
print(new_numbers)

# output
[2, 3, 4]
```

- We create a new list called `new_numbers` and assign it to the result of the list comprehension.

- The list comprehension is `[n + 1 for n in numbers]`. This means for each item in the list `numbers` add 1 to it and return the result.

- a technic in creating a list comprehension is to use the keyword method.
  `new_list = [new_item for item in list]`

- in the keyword method, we can use the `new_item` to apply a function to each item in the list.
- we can also use the `item` to filter the list.

```python
# main.py
# create a new list from an existing list by applying a function to each item in the existing list
numbers = [1, 2, 3]
new_numbers = [n * 2 for n in numbers]
print(new_numbers)

# output
[2, 4, 6]
```

- in the above example, we multiply each item in the list by 2.
- `n * 2` is the function we apply to each item in the list and it represents the `new_item` in the keyword method.

- `n` is the `item` in the keyword method and it represents each item in the list.

- `numbers` is the `list` in the keyword method and it represents the existing list.

```python
# main.py
# create a new list from an existing list by applying a function to each item in the existing list
name = "Aretas"
letters_list = [letter for letter in name]
print(letters_list)

# output
['A', 'r', 'e', 't', 'a', 's']
```

- List comprehension can also be used on strings, tuples, and dictionaries.

```python
# main.py
# create a new list from an existing list by applying a function to each item in the existing list
range_list = [n * 2 for n in range(1, 5)]
print(range_list)

# output
[2, 4, 6, 8]
```

## Conditional List Comprehension

- We can use conditional list comprehension to filter a list.

```python
# main.py
# create a new list from an existing list by applying a function to each item in the existing list
names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]
short_names = [name for name in names if len(name) < 5]
print(short_names)

# output
['Alex', 'Beth', 'Dave']
```

- In the above example, we create a new list called `short_names` and assign it to the result of the conditional list comprehension.
- The conditional list comprehension is `[name for name in names if len(name) < 5]`. This means for each item in the list `names` if the length of the item is less than 5 return the item.

- We can also use the `else` keyword in conditional list comprehension.

```python
# main.py
# create a new list from an existing list by applying a function to each item in the existing list
names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]
long_names = [name.upper() for name in names if len(name) > 5 else name.lower()]
print(long_names)

# output
['ALEX', 'BETH', 'CAROLINE', 'dave', 'eleanor', 'freddie']
```

- In the above example, we create a new list called `long_names` and assign it to the result of the conditional list comprehension.
- The conditional list comprehension is `[name.upper() for name in names if len(name) > 5 else name.lower()]`. This means for each item in the list `names` if the length of the item is greater than 5 return the item in uppercase else return the item in lowercase.

### squaring numbers

```python
# main.py

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
squared_numbers = [n ** 2 for n in numbers]
print(squared_numbers)

# output
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```

### filtering even numbers

```python
# main.py

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
even_numbers = [n for n in numbers if n % 2 == 0]
print(even_numbers)

# output
[2, 4, 6, 8]
```

### filtering odd numbers

```python
# main.py

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
odd_numbers = [n for n in numbers if n % 2 != 0]
print(odd_numbers)

# output
[1, 3, 5, 7, 9]
```

### filtering numbers greater than 3

```python
# main.py

numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9]
greater_than_3 = [n for n in numbers if n > 3]
print(greater_than_3)

# output
[4, 5, 6, 7, 8, 9]
```

### Data overlap

```python
# main.py

list_1 = [1, 2, 3]
list_2 = [3, 4, 5]
overlap = [n for n in list_1 if n in list_2]
print(overlap)

# output
[3]
```

## Dictionary Comprehension

- We can use dictionary comprehension to create a new dictionary from an existing dictionary.
- While we use square brackets `[]` in list comprehension, we use curly braces `{}` in dictionary comprehension.

```python
# main.py
# create a new dictionary from an existing dictionary
names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]
scores = [81, 78, 99, 74, 65, 82]
student_scores = {name: score for name, score in zip(names, scores)}
print(student_scores)

# output
{'Alex': 81, 'Beth': 78, 'Caroline': 99, 'Dave': 74, 'Eleanor': 65, 'Freddie': 82}
```

- In the above example, we create a new dictionary called `student_scores` and assign it to the result of the dictionary comprehension.
- The dictionary comprehension is `{name: score for name, score in zip(names, scores)}`. This means for each item in the list `names` and `scores` create a new dictionary with the item in `names` as the key and the item in `scores` as the value.

- We can also use the `if` keyword in dictionary comprehension.

```python
# main.py
# create a new dictionary from an existing dictionary
names = ["Alex", "Beth", "Caroline", "Dave", "Eleanor", "Freddie"]
scores = [81, 78, 99, 74, 65, 82]
student_scores = {name: score for name, score in zip(names, scores) if score > 80}
print(student_scores)

# output
{'Alex': 81, 'Caroline': 99, 'Freddie': 82}
```

### looping through a dictionary

```python
# main.py

student_scores = {
    "Alex": 81,
    "Beth": 78,
    "Caroline": 99,
    "Dave": 74,
    "Eleanor": 65,
    "Freddie": 82,
}

for key in student_scores:
    print(key)

# output
Alex
Beth
Caroline
Dave
Eleanor
Freddie
```

### Counting the words in a sentence

```python
# main.py

sentence = "What is the Airspeed Velocity of an Unladen Swallow?"
result = {word: len(word) for word in sentence.split()}
print(result)

# output
{'What': 4, 'is': 2, 'the': 3, 'Airspeed': 8, 'Velocity': 8, 'of': 2, 'an': 2, 'Unladen': 7, 'Swallow?': 8}
```

- In the above example, we create a new dictionary called `result` and assign it to the result of the dictionary comprehension.
- The dictionary comprehension is `{word: len(word) for word in sentence.split()}`. This means for each item in the list `sentence.split()` create a new dictionary with the item in `sentence.split()` as the key and the length of the item as the value.
- `sentence.split()` splits the sentence into a list of words.
- `len(word)` returns the length of the word.
- `word` is the `item` in the keyword method and it represents each item in the list.
- `sentence.split()` is the `list` in the keyword method and it represents the existing list.
- `word: len(word)` is the `new_item` in the keyword method and it represents the key and value in the new dictionary.
- `result` is the `new_dictionary` in the keyword method and it represents the new dictionary.

### Convert a Celsius temperature to Fahrenheit

```python
# main.py

weather_c = {
    "Monday": 12,
    "Tuesday": 14,
    "Wednesday": 15,
    "Thursday": 14,
    "Friday": 21,
    "Saturday": 22,
    "Sunday": 24,
}

weather_f = {day: (temp * 9 / 5) + 32 for (day, temp) in weather_c.items()}
print(weather_f)

# output
{'Monday': 53.6, 'Tuesday': 57.2, 'Wednesday': 59.0, 'Thursday': 57.2, 'Friday': 69.8, 'Saturday': 71.6, 'Sunday': 75.2}
```

- In the above example, we create a new dictionary called `weather_f` and assign it to the result of the dictionary comprehension.
- The dictionary comprehension is `{day: (temp * 9 / 5) + 32 for (day, temp) in weather_c.items()}`. This means for each item in the list `weather_c.items()` create a new dictionary with the item in `weather_c.items()` as the key and the value of the item converted to Fahrenheit as the value.
- `weather_c.items()` returns a list of tuples of the key and value in the dictionary.
- `(temp * 9 / 5) + 32` converts the temperature from Celsius to Fahrenheit.
- `day` is the `item` in the keyword method and it represents each item in the list.
- `weather_c.items()` is the `list` in the keyword method and it represents the existing list.
- `day: (temp * 9 / 5) + 32` is the `new_item` in the keyword method and it represents the key and value in the new dictionary.
- `weather_f` is the `new_dictionary` in the keyword method and it represents the new dictionary.

### How to iterate over a pandas DataFrame

- We can use the `pandas.DataFrame.iterrows()` function to iterate over a pandas DataFrame.

```python
# weather_data.csv
day,temp,condition
Monday,12,Sunny
Tuesday,14,Rain
Wednesday,15,Rain
Thursday,14,Cloudy
Friday,21 ,Cloudy
Saturday,22,Sunny
Sunday,24,Sunny
```

```python
# main.py
# open the weather_data.csv file and iterate over the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
for (index, row) in data.iterrows():
    print(row)

# output
day          Monday
temp             12
condition     Sunny
Name: 0, dtype: object
day         Tuesday
temp             14
condition      Rain
Name: 1, dtype: object
day         Wednesday
temp               15
condition        Rain
Name: 2, dtype: object
day         Thursday
temp              14
condition     Cloudy
Name: 3, dtype: object
day          Friday
temp             21
condition    Cloudy
Name: 4, dtype: object
day          Saturday
temp               22
condition       Sunny
Name: 5, dtype: object
day          Sunday
temp             24
condition     Sunny
Name: 6, dtype: object
```

- In the above example, we iterate over the data in the `weather_data.csv` file.
- `data.iterrows()` returns a tuple of the index and row in the DataFrame.
- `index` is the index of the row in the DataFrame.
- `row` is the row in the DataFrame.
- `print(row)` prints the row in the DataFrame.
- `print(row["day"])` prints the day column in the DataFrame.
- `print(row["temp"])` prints the temp column in the DataFrame.
- `print(row["condition"])` prints the condition column in the DataFrame.

## The NATO Alphabet Project

- We are going to create a program that converts a word to the NATO alphabet.
- The NATO alphabet is a spelling alphabet used by airline pilots, police, and the military to communicate.
- Each word in the NATO alphabet is assigned to a letter in the English alphabet.
- For example, the word "apple" is assigned to the letter "A" in the English alphabet.
- The NATO alphabet is used to spell out words.
- For example, the word "apple" is spelled out as "Alpha Papa Papa Lima Echo" in the NATO alphabet.

### The NATO alphabet dictionary

- We create a dictionary called `nato_alphabet` that contains the NATO alphabet.

```python
# nato_alphabet.py
nato_alphabet = {
    "A": "Alpha",
    "B": "Bravo",
    "C": "Charlie",
    "D": "Delta",
    "E": "Echo",
    "F": "Foxtrot",
    "G": "Golf",
    "H": "Hotel",
    "I": "India",
    "J": "Juliet",
    "K": "Kilo",
    "L": "Lima",
    "M": "Mike",
    "N": "November",
    "O": "Oscar",
    "P": "Papa",
    "Q": "Quebec",
    "R": "Romeo",
    "S": "Sierra",
    "T": "Tango",
    "U": "Uniform",
    "V": "Victor",
    "W": "Whiskey",
    "X": "X-ray",
    "Y": "Yankee",
    "Z": "Zulu",
}

# main.py
# open the nato_alphabet.py file and create a dictionary named nato_alphabet that contains the NATO alphabet
from nato_alphabet import nato_alphabet

# create a dictionary named nato_alphabet that contains the NATO alphabet

# output
{'A': 'Alpha', 'B': 'Bravo', 'C': 'Charlie', 'D': 'Delta', 'E': 'Echo', 'F': 'Foxtrot', 'G': 'Golf', 'H': 'Hotel', 'I': 'India', 'J': 'Juliet', 'K': 'Kilo', 'L': 'Lima', 'M': 'Mike', 'N': 'November', 'O': 'Oscar', 'P': 'Papa', 'Q': 'Quebec', 'R': 'Romeo', 'S': 'Sierra', 'T': 'Tango', 'U': 'Uniform', 'V': 'Victor', 'W': 'Whiskey', 'X': 'X-ray', 'Y': 'Yankee', 'Z': 'Zulu'}
```

### The NATO alphabet project

- We create a program that converts a word to the NATO alphabet.

```python
# main.py
# open the nato_alphabet.py file and create a dictionary named nato_alphabet that contains the NATO alphabet
from nato_alphabet import nato_alphabet

# create a dictionary named nato_alphabet that contains the NATO alphabet

# create a program that converts a word to the NATO alphabet
word = input("Enter a word: ").upper()
nato_word = [nato_alphabet[letter] for letter in word]
print(nato_word)

# output
Enter a word: apple
['Alpha', 'Papa', 'Papa', 'Lima', 'Echo']
```
