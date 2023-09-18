---
layout: post
title: 100 Days Of Python - Day 28
date: 2023-09-09 18:22 +0000
categories: [Python Tutorial, Day 28]
tags: [day 28, canvas, dynamic typing, pomodora app]
---

## Day 28

## Tkinter Canvas

- The canvas widget is used to draw shapes, such as lines, ovals, polygons and rectangles, in your application. The canvas widget can also be used to create graphs and plots.
- The canvas widget works with vector graphics and not with bitmaps.
- It helps us create images, lines, rectangles, ovals, and text in layers.

## Dynamic Typing

- Python is a dynamically typed language. This means that the Python interpreter does type checking only as code runs, and that the type of a variable is allowed to change over its lifetime.
- The following code is valid in Python −

```python
a = 5
a = "Hello World!"
```

- We are able to dynamically change a vairiable type and this is called `Dynamic Typing`.

## Pomodora App

{: .prompt-info }

> - Pomodora is a technique where you work for 25 minutes and then take a 5 minute break. After 4 such cycles, you take a 15 minute break.
> - It is a productivity technique that helps you focus on your work.
> - We will use the `after()` method to create a timer that will run every second and update the timer.
> - We will use the `canvas.itemconfig()` method to update the timer text.

```python
from tkinter import *
import math

# ---------------------------- CONSTANTS ------------------------------- #
PINK = "#D864A9"
RED = "#862B0D"
GREEN = "#335D2D"
YELLOW = "#E5FDD1"
FONT_NAME = "Courier"
WORK_MIN = 25
SHORT_BREAK_MIN = 5
LONG_BREAK_MIN = 20
reps = 0
timer = None


# ---------------------------- TIMER RESET ------------------------------- #

def reset_timer():
    window.after_cancel(timer)
    timer_label.config(text="Timer", fg=GREEN)
    canvas.itemconfig(timer_text, text="00:00")
    check_mark.config(text="")
    global reps
    reps = 0


# ---------------------------- TIMER MECHANISM ------------------------------- #
def start_timer():
    global reps
    reps += 1
    work_sec = WORK_MIN * 60
    short_break_sec = SHORT_BREAK_MIN * 60
    long_break_sec = LONG_BREAK_MIN * 60

    if reps % 8 == 0:
        count_down(long_break_sec)
        timer_label.config(text="Break", fg=RED)
    elif reps % 2 == 0:
        count_down(short_break_sec)
        timer_label.config(text="Break", fg=PINK)
    else:
        count_down(work_sec)
        timer_label.config(text="Work", fg=GREEN)


# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #


def count_down(count):
    count_min = math.floor(count / 60)
    count_sec = count % 60
    canvas.itemconfig(timer_text, text=f"{count_min:02}:{count_sec:02}")
    # canvas.itemconfig(timer_text, text=f"{count_min}:{'{:02d}'.format(count_sec)}")
    if count > 0:
        global timer
        timer = window.after(1000, count_down, count - 1)
    else:
        start_timer()
        marks = ""
        work_sessions = math.floor(reps / 2)
        for _ in range(work_sessions):
            marks += "✔"
        check_mark.config(text=marks)


# ---------------------------- UI SETUP ------------------------------- #
window = Tk()
window.title("Pomodoro")
window.config(padx=100, pady=50, bg=YELLOW)

# Labels
timer_label = Label(text="Timer", fg=GREEN, bg=YELLOW, font=(FONT_NAME, 50))
timer_label.grid(column=1, row=0)

# Canvas
canvas = Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)
tomato_img = PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)
timer_text = canvas.create_text(100, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))
canvas.grid(column=1, row=1)

# Buttons
start_button = Button(text="Start", command=start_timer, highlightthickness=0)
start_button.grid(column=0, row=2)

reset_button = Button(text="Reset", highlightthickness=0, command=reset_timer)
reset_button.grid(column=2, row=2)

check_mark = Label(fg=GREEN, bg=YELLOW, font=(FONT_NAME, 20))
check_mark.grid(column=1, row=3)

window.mainloop()
```
