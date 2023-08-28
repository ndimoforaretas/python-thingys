---
layout: post
title: 100 Days Of Python - Day 19
date: 2023-08-27 17:57 +0000
categories: [Python Tutorial, Day 19]
tags: [day 19, higher order functions, event listeners, state, turtle race]
---

## Day 19

## Higher order functions and event listeners

### Higher order functions

- A higher order function is a function that can accept other functions as arguments and/or return functions as output.
- We can do this by passing the function name without the parentheses. For example:

```python
def add(n1, n2):
  return n1 + n2

def subtract(n1, n2):
    return n1 - n2

def multiply(n1, n2):
    return n1 * n2

def divide(n1, n2):
    return n1 / n2

def calculator(n1, n2, func):
    return func(n1, n2)

result = calculator(2, 3, add)
print(result)

# 5
```

- We can also pass functions as inputs into other functions like map(), filter() and reduce().
- For example:

```python
from functools import reduce

def my_function(a, b):
    return a + b

my_list = [1, 2, 3]

result = reduce(my_function, my_list)
print(result)

# 6
```

### Event listeners

- An event listener is a procedure or function in a computer program that waits for an event to occur.
- For example, if a user clicks a button, the click is an event.
- The listener waits for the click to occur and then triggers an action.
- We can use the `turtle` module to create a simple drawing program.
- For example:

```python
from turtle import Turtle, Screen

tim = Turtle()
screen = Screen()


def move_forwards():
    tim.forward(10)


def move_backwards():
    tim.backward(10)


def turn_left():
    new_heading = tim.heading() + 10
    tim.setheading(new_heading)


def turn_right():
    new_heading = tim.heading() - 10
    tim.setheading(new_heading)


def clear():
    tim.clear()
    tim.penup()
    tim.home()
    tim.pendown()


screen.listen()
screen.onkey(move_forwards, "w")
screen.onkey(move_backwards, "s")
screen.onkey(turn_left, "a")
screen.onkey(turn_right, "d")
screen.onkey(clear, "c")
screen.exitonclick()
```

## State

- The state of an object is the combination of all the attributes of an object.
- For example, the state of a car is the combination of all the attributes of the car.
- The state of a car includes the make, model, color, mileage, etc.
- The state of a car can change over time.
- For example, the mileage of a car can increase over time.
- We can use the `turtle` module to create a simple drawing program.

## The turtle race project

- We can use the `turtle` module to create a simple racing program.

```python
from turtle import Turtle, Screen
import random

screen = Screen()
is_race_on = False
screen.setup(width=500, height=400)
user_choice = screen.textinput(title="Choose a runner", prompt="Which turtle do you think will win (red, orange, "
                                                               "black, green, blue, purple? Enter a color: ")
colors = ["red", "orange", "black", "green", "blue", "purple"]
y_positions = [-70, -40, -10, 20, 50, 80]
all_turtles = []

for turtle_index in range(0, 6):
    new_turtle = Turtle(shape="turtle")
    new_turtle.penup()
    new_turtle.color(colors[turtle_index])
    new_turtle.setposition(x=-230, y=y_positions[turtle_index])
    all_turtles.append(new_turtle)

if user_choice:
    is_race_on = True

while is_race_on:

    for turtle in all_turtles:
        if turtle.xcor() > 230:
            is_race_on = False
            winning_color = turtle.pencolor()
            if winning_color == user_choice:
                print(f"You've won! The {winning_color} turtle is the winner!")
            else:
                print(f"You've lost! The {winning_color} turtle is the winner!")

    for turtle in all_turtles:
        random_distance = random.randint(0, 10)
        turtle.forward(random_distance)

screen.exitonclick()
```
