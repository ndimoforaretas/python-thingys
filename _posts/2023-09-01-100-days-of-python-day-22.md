---
layout: post
title: 100 Days Of Python - Day 22
date: 2023-09-01 13:35 +0000
categories: [Python Tutorial, Day 22]
tags: [day 22]
---

## Day 22

### Day 22 Project - Pong Game

#### Starting screen

The starting screen is going to have the following properties:

- a width of 800 pixels
- a height of 600 pixels
- a black background
- it should stay on the screen until the user clicks on it

```python
from turtle import Screen, Turtle

screen = Screen()
screen.setup(width=800, height=600)
screen.bgcolor("black")
screen.title("Pong")



screen.exitonclick()
```

#### Create and move the paddles

The paddles are going to have the following properties:

- a width of 20 pixels
- a height of 100 pixels
- a white color
- a starting position of (350, 0) for the right paddle
- a starting position of (-350, 0) for the left paddle
- the user should be able to move the paddles up and down using the `up` and `down` arrow keys

```python

# paddle.py
from turtle import Turtle


class Paddle(Turtle):

    def __init__(self, position):
        super().__init__()
        self.shape("square")
        self.color("white")
        self.shapesize(stretch_wid=5, stretch_len=1)
        self.penup()
        self.goto(position)

    def move_up(self):
        new_y = self.ycor() + 20
        self.goto(self.xcor(), new_y)

    def move_down(self):
        new_y = self.ycor() - 20
        self.goto(self.xcor(), new_y)



# main.py
from turtle import Screen, Turtle
from paddle import Paddle

screen = Screen()
screen.setup(width=800, height=600)
screen.bgcolor("black")
screen.title("Pong")
screen.tracer(0)

r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))



screen.listen()
screen.onkey(r_paddle.move_up(), "Up")
screen.onkey(r_paddle.move_down(), "Down")
screen.onkey(l_paddle.move_up(), "w")
screen.onkey(l_paddle.move_down(), "s")

game_is_on = True
while game_is_on:
    screen.update()




screen.exitonclick()
```

#### Create the ball and make it move

The ball is going to have the following properties:

- a width of 20 pixels
- a height of 20 pixels
- a white color
- a starting position of (0, 0)
- it should move at 10 paces per second
- it should bounce off the top and bottom walls
- it should bounce off the paddles
- if the ball misses the paddle, the game should restart

```python
# ball.py
from turtle import Turtle


class Ball(Turtle):

    def __init__(self):
        super().__init__()
        self.shape("square")
        self.color("white")
        self.penup()
        self.x_move = 10
        self.y_move = 10

    def move(self):
        new_x = self.xcor() + self.x_move
        new_y = self.ycor() + self.y_move
        self.goto(new_x, new_y)

    def bounce(self):
        self.y_move *= -1

    def bounce_back(self):
        self.x_move *= -1

    def reset_position(self):
        self.goto(0, 0)
        self.bounce_back()

# main.py
from turtle import Screen, Turtle
from paddle import Paddle
from ball import Ball
import time

screen = Screen()
screen.setup(width=800, height=600)
screen.bgcolor("black")
screen.title("Pong")
screen.tracer(0)

r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))
ball = Ball()

screen.listen()
screen.onkey(r_paddle.move_up, "Up")
screen.onkey(r_paddle.move_down, "Down")
screen.onkey(l_paddle.move_up, "w")
screen.onkey(l_paddle.move_down, "s")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    screen.update()
    ball.move()

    # Detect collision with wall
    if ball.ycor() > 280 or ball.ycor() < -280:
        ball.bounce()

    # Detect collision with paddle
    if ball.distance(r_paddle) < 50 and ball.xcor() > 320 or ball.distance(l_paddle) < 50 and ball.xcor() < -320:
        ball.bounce_back()

    # Detect when right paddle misses
    if ball.xcor() > 380:
        ball.reset_position()

    # Detect when left paddle misses
    if ball.xcor() < -380:
        ball.reset_position()


screen.exitonclick()
```
