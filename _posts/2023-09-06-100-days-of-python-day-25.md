---
layout: post
title: 100 Days Of Python - Day 25
date: 2023-09-06 05:30 +0000
categories: [Python Tutorial, Day 25]
tags: [day 25, csv, pandas, series, data frame, squirrel census, us states game]
---

## Day 25

### Reading and writing CSV files in python

In python, we can use the `csv` module to read and write CSV files.

- CSV stands for Comma Separated Values.
- CSV files are text files that store tabular data.
- CSV files are commonly used to store data in spreadsheets.

```python
# weather_data.csv
 day,temp,condition
 Monday,12,Sunny
 Tuesday,14,Rain
 Wednesday,15,Rain
 Thursday,14,Cloudy
 Friday,21,Cloudy
 Saturday,22,Sunny
 Sunday,24,Sunny


# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import csv

with open("weather_data.csv") as file:
    data = csv.reader(file)
    temperatures = []
    for row in data:
        if row[1] != "temp":
            temperatures.append(int(row[1]))
    print(temperatures)

    # output
    # [12, 14, 15, 14, 21, 22, 24]
```

- The `csv.reader()` function returns a reader object that iterates over lines in the CSV file.
- In the above example our objective is to:
  - read the CSV file
  - extract the temperatures
  - store the temperatures in a list
  - print the list of temperatures

## Pandas

Pandas is a python library that is used for data analysis.

- Pandas is a third-party library and therefore we need to install it before we can use it.

```bash
pip install pandas
```

- If we wish to use pandas to fullfil the objective of the previous example, we can do so as follows:

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data["temp"]) # prints the temp column in the CSV file

# output
# 0    12
# 1    14
# 2    15
# 3    14
# 4    21
# 5    22
# 6    24
# Name: temp, dtype: int64
```

- The `pandas.read_csv()` function returns a DataFrame object that contains the data in the CSV file.
- A `DataFrame` is a `2-dimensional` data structure that is similar to a `spreadsheet`.
- When we print just the `temp` column, we get a `Series object`.
- A `Series` is a `1-dimensional` data structure that is similar to a `list`.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(type(data)) # prints the type of data
print(type(data["temp"])) # prints the type of data["temp"]

# output
# <class 'pandas.core.frame.DataFrame'> # data is a DataFrame
# <class 'pandas.core.series.Series'> # data["temp"] is a Series
```

- We can use the `pandas.DataFrame.to_dict()` function to convert a DataFrame to a dictionary.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data.to_dict()) # prints the data in the CSV file as a dictionary

# output
# {'day': {0: 'Monday', 1: 'Tuesday', 2: 'Wednesday', 3: 'Thursday', 4: 'Friday', 5: 'Saturday', 6: 'Sunday'}, 'temp': {0: 12, 1: 14, 2: 15, 3: 14, 4: 21, 5: 22, 6: 24}, 'condition': {0: 'Sunny', 1: 'Rain', 2: 'Rain', 3: 'Cloudy', 4: 'Cloudy', 5: 'Sunny', 6: 'Sunny'}}
```

- We can use the `pandas.DataFrame[column_name]` syntax to access a column in a DataFrame.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data["temp"]) # prints the temp column in the CSV file

# output
# 0    12
# 1    14
# 2    15
# 3    14
# 4    21
# 5    22
# 6    24
# Name: temp, dtype: int64
```

- We can use the `pandas.DataFrame[column_name].to_list()` function to convert a column in a DataFrame to a list.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data["temp"].to_list()) # prints the temp column in the CSV file as a list

# output
# [12, 14, 15, 14, 21, 22, 24]
```

- We can use the `pandas.DataFrame[column_name].mean()` function to calculate the mean of a column in a DataFrame.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data["temp"].mean()) # prints the mean of the temp column in the CSV file

# output
# 17.428571428571427
```

- We can use the `pandas.DataFrame[column_name].max()` function to calculate the maximum value of a column in a DataFrame.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data["temp"].max()) # prints the maximum value of the temp column in the CSV file

# output
# 24
```

### Get Data in Row

- We can use the `pandas.DataFrame[pandas.DataFrame[column_name] == value]` syntax to get a row in a DataFrame.

```python
# main.py
# open the weather_data.csv file and create a list named data that contains the data in the file
import pandas

data = pandas.read_csv("weather_data.csv")
#print(data) # prints the data in the CSV file
print(data[data["day"] == "Monday"]) # prints the row in the CSV file where the day is Monday

# output
#       day  temp condition
# 0  Monday    12     Sunny
```

### Create a DataFrame from scratch

- We can use the `pandas.DataFrame()` function to create a DataFrame from scratch.

```python
# main.py
# create a DataFrame from scratch
import pandas

data_dict = {
    "students": ["Amy", "James", "Angela"],
    "scores": [76, 56, 65]
}

data = pandas.DataFrame(data_dict)
print(data)

# output
#   students  scores
# 0      Amy      76
# 1    James      56
# 2   Angela      65
```

### Create a CSV file from a DataFrame

- We can use the `pandas.DataFrame.to_csv()` function to create a CSV file from a DataFrame.

```python
# main.py
# create a CSV file from a DataFrame
import pandas

data_dict = {
    "students": ["Amy", "James", "Angela"],
    "scores": [76, 56, 65]
}

data = pandas.DataFrame(data_dict)
data.to_csv("new_data.csv")

# output
# new_data.csv
# ,students,scores
# 0,Amy,76
# 1,James,56
# 2,Angela,65
```

## Squirrel Census Data Analysis

- We can use the `pandas.DataFrame[column_name].value_counts()` function to get the number of times a value appears in a column in a DataFrame.

```python
# main.py
# analyze the squirrel census data
import pandas

data = pandas.read_csv("2018_Central_Park_Squirrel_Census_-_Squirrel_Data.csv")
#print(data) # prints the data in the CSV file
gray_squirrels_count = len(data[data["Primary Fur Color"] == "Gray"])
red_squirrels_count = len(data[data["Primary Fur Color"] == "Cinnamon"])
black_squirrels_count = len(data[data["Primary Fur Color"] == "Black"])
print(gray_squirrels_count) # prints the number of gray squirrels
print(red_squirrels_count) # prints the number of red squirrels
print(black_squirrels_count) # prints the number of black squirrels

data_dict = {
    "Fur Color": ["Gray", "Cinnamon", "Black"],
    "Count": [gray_squirrels_count, red_squirrels_count, black_squirrels_count]
}

data = pandas.DataFrame(data_dict)
data.to_csv("squirrel_count.csv")

# output

# 2473
# 392
# 103
```

## Us States Game

This is a game that tests your knowledge of the US states.
The game will prompt you to name a state.
If you name a state correctly, the state will be marked on the map.
If you name a state incorrectly, the game will end and a CSV file containing the names of the states you missed will be created.

```python
import turtle
import pandas

# Create a turtle
screen = turtle.Screen()
screen.title("U.S. States Game")
image = "blank_states_img.gif"
screen.addshape(image)
turtle.shape(image)

data = pandas.read_csv("50_states.csv")
all_states = data.state.to_list()
guessed_states = []

# Game loop
while len(guessed_states) < 50:
    answer_state = screen.textinput(title=f"{len(guessed_states)}/50 States Correct",
                                    prompt="What's another state's name?").title()

    # Exit game
    if answer_state == "Exit":
        missing_states = [state for state in all_states if state not in guessed_states]
        new_data = pandas.DataFrame(missing_states)
        new_data.to_csv("states_to_learn.csv")
        break

    # Check answer
    if answer_state in all_states:
        guessed_states.append(answer_state)
        t = turtle.Turtle()
        t.hideturtle()
        t.penup()
        state_data = data[data.state == answer_state]
        t.goto(int(state_data.x), int(state_data.y))
        t.write(answer_state)


```
