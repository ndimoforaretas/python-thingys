---
layout: post
title: 100 Days Of Python - Day 21
date: 2023-08-29 18:59 +0000
categories: [Python Tutorial, Day 21]
tags: [day 21, snake game, turtle graphics, class inheritance, slicing lists]
---

## Day 21

## Class Inheritance

### Inheritance

- Inheritance is a way to create a new class from an existing class.
- The new class is called the **child** class and the existing class is called the **parent** class.
- The child class inherits all of the attributes and methods of the parent class.
- The child class can also have its own attributes and methods.
- The child class can also override the attributes and methods of the parent class.
- The child class can also add new attributes and methods to the parent class.

### Creating a Child Class

- To create a child class, we pass the parent class as an argument to the child class.

```python
class ChildClass(ParentClass):
    # Child class code
```

- For example, we can create a `Fish` class that inherits from the `Animal` class.

```python
class Fish(Animal):
    # Fish class code
```

- The `Fish` class will inherit all of the attributes and methods of the `Animal` class.
- We can then add new attributes and methods to the `Fish` class.

```python
class Animal:
    def __init__(self):
        self.eyes = 2
        self.legs = 4

    def breathe(self):
        print("The animal is breathing.")

    def eat(self):
        print("The animal is eating.")

class Fish(Animal):
    def __init__(self):
        super().__init__()
        self.fins = 2

    def swim(self):
        print("The fish is swimming.")
```

- The `Fish` class has a new attribute called `fins` and a new method called `swim()`.
- The `Fish` class also has all of the attributes and methods of the `Animal` class.
- The `super()` function is used to call the `__init__()` method of the parent class. This allows us to use the attributes and methods of the parent class in the child class.

### Overriding Methods

- We can override the methods of the parent class in the child class.

```python
class Fish(Animal):
    def __init__(self):
        super().__init__()
        self.fins = 2

    def swim(self):
        print("The fish is swimming.")

    def breathe(self):
        print("The fish is breathing through its gills.")
```

- The `Fish` class overrides the `breathe()` method of the `Animal` class.
- The `Fish` class has a new `breathe()` method that prints "The fish is breathing through its gills."

## Slicing Lists

### Slicing Lists

- We can use slicing to get a subset of a list.
- We can use slicing to get a subset of a list from a starting index to an ending index.
- We can also use slicing to get a subset of a list from a starting index to an ending index with a step size.
- We can also use slicing to get a subset of a list from a starting index to an ending index with a step size in reverse order.

```python
# Get a subset of a list from a starting index to an ending index
list[start:end]

# Get a subset of a list from a starting index to an ending index with a step size
list[start:end:step]

# Get a subset of a list from a starting index to an ending index with a step size in reverse order
list[start:end:-step]
```

- The starting index is inclusive.
- The ending index is exclusive.
- The step size is the number of elements to skip.
- The step size can be negative to go in reverse order.

For example, we can use slicing to get a subset of a list from a starting index to an ending index.

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Get a subset of a list from a starting index to an ending index
print(numbers[2:5])

# Output: [3, 4, 5]
```

- The starting index is 2.
- The ending index is 5.

We can also use slicing to get a subset of a list from a starting index to an ending index with a step size.

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Get a subset of a list from a starting index to an ending index with a step size
print(numbers[2:8:2])

# Output: [3, 5, 7]
```

- The starting index is 2.
- The ending index is 8.
- The step size is 2.

We can also use slicing to get a subset of a list from a starting index to an ending index with a step size in reverse order.

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Get a subset of a list from a starting index to an ending index with a step size in reverse order
print(numbers[8:2:-2])

# Output: [9, 7, 5]
```

- The starting index is 8.
- The ending index is 2.
- The step size is -2.

- Slicing also works with Tuple and String objects. For example:

```python
# Slicing a Tuple

tuple = (1, 2, 3, 4, 5, 6, 7, 8, 9, 10)

# Get a subset of a tuple from a starting index to an ending index
print(tuple[2:5])

# Output: (3, 4, 5)

# Get a subset of a tuple from a starting index to an ending index with a step size
print(tuple[2:8:2])

# Output: (3, 5, 7)

# Get a subset of a tuple from a starting index to an ending index with a step size in reverse order
print(tuple[8:2:-2])

# Output: (9, 7, 5)

# Slicing a String

string = "Hello World"

# Get a subset of a string from a starting index to an ending index
print(string[2:5])

# Output: llo

# Get a subset of a string from a starting index to an ending index with a step size
print(string[2:8:2])

# Output: loW

# Get a subset of a string from a starting index to an ending index with a step size in reverse order
print(string[8:2:-2])
```

## Snake Game Part 2

- Create the Food

- Create a food class using the `Turtle` module, in the `food.py` file.

```python
from turtle import Turtle
import random

class Food(Turtle):
    def __init__(self):
        super().__init__()
        self.shape("circle")
        self.penup()
        self.shapesize(stretch_len=0.5, stretch_wid=0.5)
        self.color("blue")
        self.speed("fastest")
        self.refresh()

    def refresh(self):
        random_x = random.randint(-280, 280)
        random_y = random.randint(-280, 280)
        self.goto(random_x, random_y)
```

- snake.py

```python
from turtle import Turtle

STARTING_POSITIONS = [(0, 0), (-20, 0), (-40, 0)]
MOVE_DISTANCE = 20
UP = 90
DOWN = 270
LEFT = 180
RIGHT = 0


class Snake:
    def __init__(self):
        self.segments = []
        self.create_snake()
        self.head = self.segments[0]

    def create_snake(self):

        for position in STARTING_POSITIONS:
            self.add_segment(position)

    def add_segment(self, position):
        new_segment = Turtle("square")
        new_segment.color("white")
        new_segment.penup()
        new_segment.goto(position)
        self.segments.append(new_segment)

    def extend(self):
        # Add a new segment to the snake
        self.add_segment(self.segments[-1].position())

    def move(self):
        # Move the snake
        for seg_num in range(len(self.segments) - 1, 0, -1):
            new_x = self.segments[seg_num - 1].xcor()
            new_y = self.segments[seg_num - 1].ycor()
            self.segments[seg_num].goto(new_x, new_y)
        self.segments[0].forward(MOVE_DISTANCE)

    def up(self):
        if self.head.heading() != DOWN:
            self.head.setheading(UP)

    def down(self):
        if self.head.heading() != UP:
            self.head.setheading(DOWN)

    def left(self):
        if self.head.heading() != RIGHT:
            self.head.setheading(LEFT)

    def right(self):
        if self.head.heading() != LEFT:
            self.head.setheading(RIGHT)
```

- scoreboard.py

```python
from turtle import Turtle

ALIGNMENT = "center"
FONT = ("Roboto", 24, "normal")


# Create a scoreboard class that inherits from the Turtle class
class Scoreboard(Turtle):
    # Create a constructor method that inherits from the Turtle class
    def __init__(self):
        super().__init__()
        # Create a score attribute
        self.score = 0
        # Create a high score attribute
        self.high_score = 0
        # Create a scoreboard object
        self.penup()
        # Hide the scoreboard object
        self.hideturtle()
        # Move the scoreboard object to the top of the screen
        self.goto(0, 270)
        # Change the color of the scoreboard object
        self.color("white")
        # Update the scoreboard object
        self.update_scoreboard()

    # Update the scoreboard object
    def update_scoreboard(self):
        # Clear the scoreboard object
        self.clear()
        # Write the score on the scoreboard object
        self.write(f"Score: {self.score} High Score: {self.high_score}", align=ALIGNMENT, font=FONT)

    # Reset the scoreboard object
    def reset(self):
        # Check if the score is greater than the high score
        if self.score > self.high_score:
            # Set the high score to the score
            self.high_score = self.score
        # Set the score to 0
        self.score = 0
        # Update the scoreboard object
        self.update_scoreboard()

    # Increase the score by 1
    def increase_score(self):
        # Increase the score by 1
        self.score += 1
        # Update the scoreboard object
        self.update_scoreboard()

    # Game over
    def game_over(self):
        # Move the scoreboard object to the center of the screen
        self.goto(0, 0)
        # Write the score on the scoreboard object
        self.write("GAME OVER", align=ALIGNMENT, font=FONT)
```

- main.py

```python
from turtle import Screen
from snake import Snake
from food import Food
from scoreboard import Scoreboard
import time

screen = Screen()
screen.setup(width=600, height=600)
screen.bgcolor("black")
screen.title("Snake Game")
screen.tracer(0)

snake = Snake()
food = Food()
scoreboard = Scoreboard()

screen.listen()
screen.onkey(snake.up, "Up")
screen.onkey(snake.down, "Down")
screen.onkey(snake.right, "Right")
screen.onkey(snake.left, "Left")

# Move the snake
game_is_on = True
while game_is_on:
    screen.update()
    time.sleep(0.1)
    snake.move()

    # Detect collision with food
    if snake.head.distance(food) < 15:
        food.new_food()
        snake.extend()
        scoreboard.increase_score()

    # Detect collision with wall
    if snake.head.xcor() > 280 or snake.head.xcor() < -290 or snake.head.ycor() > 290 or snake.head.ycor() < -280:
        game_is_on = False
        scoreboard.game_over()

    # Detect collision with tail
    for segment in snake.segments[1:]:
        if snake.head.distance(segment) < 10:
            game_is_on = False
            scoreboard.game_over()

# Exit the screen
screen.exitonclick()

```
