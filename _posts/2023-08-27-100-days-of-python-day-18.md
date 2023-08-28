---
layout: post
title: 100 Days Of Python - Day 18
date: 2023-08-27 11:33 +0000
categories: [Python Tutorial, Day 18]
tags: [day 18, importing modules, installing packages, turtle graphics, tuples]
---

## Day 18

## Importing Modules

- Modules are files containing Python code.
- Modules are used to organize code into logical groups.

### Basic Import

- The basic syntax for importing a module is:

```python
import module_name

```

- This allows you to access the module's objects using dot notation.
- For example, if we want to import the `math` module, we can do so by typing:

```python
import math

pi = math.pi

print(pi)

```

- This import method is recommended when you want to use most or all of the objects in a module.
- But if you only want to use one or two objects from a module, you can use the advanced import method.

### Advanced Import using `from`

- Another way to import a module is:

```python
from module_name import object_name

```

- This allows you to import a specific object from a module.
- It begins with the `from` keyword, followed by the module name, the `import` keyword, and finally the object name.
- If you want to import multiple objects from a module, you can do so by separating the object names with commas:

```python
from module_name import first_object, second_object

```

- When we import a module this way, we don't have to use dot notation. We can access the objects directly. For example:

```python
from math import pi

print(pi)

```

### Advanced Import using `*`

- Another way to import a module is:

```python
from module_name import *

```

- This allows you to import all the objects from a module.
- It begins with the `from` keyword, followed by the module name, the `import` keyword, and finally the `*` symbol.
- This method is not recommended because it can lead to name conflicts and also makes it difficult to know which objects are being used in a program. For example:

```python
from math import *

print(pi) # This will print the value of pi, but we don't know where it came from.

```

### Advanced Import using `as`

- Another way to import a module is:

```python
import module_name as alias

```

- This allows you to import a module with an alias. For example:

```python
import math as m

print(m.pi)

```

- This method is useful when you want to use a module with a long name, or when you want to use a module with a name that conflicts with another module.

## Installing Packages

- When we import a module which has not been installed on our computer, we get an error message.
- For example, if we try to import the `requests` module, we get the following error message:

```python
ModuleNotFoundError: No module named 'requests'

```

- We therefore need to install the `requests` module before we can use it.
- We can install the `requests` module using the `pip` command. For example:

```python
pip install requests

```

- On pycharm, we can install the `requests` module by clicking on the `Install` button in the error message.

## Turtle Graphics

### Turtle Square

- The following program draws a red square using the turtle module:

```python
from turtle import Turtle, Screen

tim = Turtle()
tim.shape("turtle")
tim.color("red")

# Draw a square
# timmy_the_turtle.forward(100)
# timmy_the_turtle.right(90)
# timmy_the_turtle.forward(100)
# timmy_the_turtle.right(90)
# timmy_the_turtle.forward(100)
# timmy_the_turtle.right(90)
# timmy_the_turtle.forward(100)

for _ in range(4):
    tim.forward(100)
    tim.right(90)

screen = Screen()
screen.exitonclick()

```

### Turtle Dashed Line

- The following program draws a dashed line using the turtle module:

```python
from turtle import Turtle, Screen

tim = Turtle()
tim.shape("turtle")
tim.color("red")

# Draw a dashed line
for _ in range(15):
    tim.forward(10)
    tim.penup()
    tim.forward(10)
    tim.pendown()

screen = Screen()
screen.exitonclick()

```

### Turtle Shapes

- The following program draws different shapes with random colors using using the turtle module:

```python
from turtle import Turtle, Screen

import random

tim = Turtle()
tim.shape("turtle")
tim.color("red")

 # Draw different shapes

 colors = ["red", "navy", "dark green", "indigo", "dark goldenrod", "purple", "pink", "dark slate gray", "black", "brown"]


def draw_shape(num_sides):
    angle = 360 / num_sides
    for _ in range(num_sides):
        tim.forward(100)
        tim.right(angle)


for shape_side_n in range(3, 11):
    tim.color(random.choice(colors))
    draw_shape(shape_side_n)

 screen = Screen()
 screen.exitonclick()
```

### Turtle Random Walk

- The following program draws a random walk using the turtle module:

```python
#colors = ["red", "navy", "dark green", "indigo", "dark goldenrod", "purple", "pink", "dark slate gray", "black", "brown"]
directions = [0, 90, 180, 270]
tim.pensize(10)
tim.speed("fastest")
screen = Screen()
screen.colormode(255)

# Generate a random color
def random_color():
    r = random.randint(0, 255)
    g = random.randint(0, 255)
    b = random.randint(0, 255)
    random_color = (r, g, b)
    return random_color


def random_walk():
    #tim.color(random.choice(colors))
    tim.color(random_color())
    tim.forward(30)
    tim.setheading(random.choice(directions))


for _ in range(200):
    random_walk()

screen.exitonclick()
```

## Tuples

- Tuples are immutable lists.
- Tuples are created using round brackets.
- Tuples are used to store data that should not be changed. For example, the days of the week or data that we don't want to change like the coordinates of a point.
- Tuples are faster than lists.

### Creating Tuples

- Tuples are created using round brackets.
- For example:

```python

# Create a tuple
my_tuple = (1, 2, 3, 4, 5)


print(my_tuple[3])

# Output:
# 4

# Create a tuple with one element
my_tuple = (1,)

print(my_tuple)

# Output:
# (1,)


```

### Turtle Spirograph

- The following program draws a spirograph using the turtle module:

```python
from turtle import Turtle, Screen

import random

tim = Turtle()
tim.shape("turtle")
tim.color("red")

tim.speed("fastest")


def random_color():
    r = random.randint(0, 255)
    g = random.randint(0, 255)
    b = random.randint(0, 255)
    random_color = (r, g, b)
    return random_color


def draw_spirograph(size_of_gap):
    for _ in range(int(360 / size_of_gap)):
        tim.color(random_color())
        tim.circle(100)
        tim.setheading(tim.heading() + size_of_gap)


draw_spirograph(5)

screen = Screen()
screen.exitonclick()
```

### Hirst Painting

- The following program draws a Hirst painting using the turtle module:

```python
import turtle as turtle_module
import random

turtle_module.colormode(255)
tim = turtle_module.Turtle()
color_list = [(202, 164, 109), (150, 75, 49), (223, 201, 135), (52, 93, 124), (171, 153, 42), (141, 178, 203)]

tim.penup()
tim.hideturtle()
tim.speed("fast")
tim.setheading(225)
tim.forward(300)
tim.setheading(0)
number_of_dots = 100

for dot_count in range(1, number_of_dots + 1):
    tim.dot(20, random.choice(color_list))
    tim.forward(50)
    if dot_count % 10 == 0:
        tim.setheading(90)
        tim.forward(50)
        tim.setheading(180)
        tim.forward(500)
        tim.setheading(0)

screen = turtle_module.Screen()
screen.exitonclick()
```
