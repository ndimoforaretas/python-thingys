---
layout: post
title: 100 Days Of Python - Day 27
date: 2023-09-08 03:48 +0000
categories: [Python Tutorial, Day 27]
tags:
  [
    day 27,
    optional arguments,
    default arguments,
    unlimited positional arguments,
    args,
    kwargs,
    pack,
    grid,
    place,
    mile to km converter,
  ]
---

## Day 27

## Optional and defualt arguments in functions

### Optional arguments

- when we define a function with optional arguments, we can set default values for the optional arguments.
- when we call the function, we can pass values for the optional arguments.
- if we do not pass values for the optional arguments, the default values will be used.

```python
# main.py
def greet(name="User", location="Earth"):
    print(f"Hello {name}")
    print(f"What is it like in {location}?")

greet() # Hello User
        # What is it like in Earth?
greet("John", "Mars") # Hello John
                      # What is it like in Mars?
```

- If we pass just one argument, the first argument will be assigned to the first optional argument and the second optional argument will be assigned the default value.

```python
# main.py
def greet(name="User", location="Earth"):
    print(f"Hello {name}")
    print(f"What is it like in {location}?")

greet("John") # Hello John
              # What is it like in Earth?
```

### Default arguments

- when we define a function with default arguments, we can set default values for the default arguments.
- when we call the function, we can pass values for the default arguments.
- if we do not pass values for the default arguments we will get an error.

```python
# main.py
def greet(name, location="Earth"):
    print(f"Hello {name}")
    print(f"What is it like in {location}?")

greet("John") # Hello John
              # What is it like in Earth?

greet() # TypeError: greet() missing 1 required positional argument: 'name'
```

### Unlimited positional arguments

#### `*args`

- `*args` is a parameter that allows us to pass an arbitrary number of arguments to a function.
- `*args` is short for **arguments**.
- `*args` returns a tuple.
- For example, if we pass `1, 2, 3, 4, 5` to the function, `*args` will return `(1, 2, 3, 4, 5)`.

```python
# main.py

def add(*args):
    total = 0
    for n in args:
        total += n
    return total

print(add(1, 2, 3, 4, 5)) # 15
```

#### `**kwargs`

- `**kwargs` is a parameter that allows us to pass an arbitrary number of keyword arguments to a function.
- `**kwargs` is short for **keyword arguments**.
- `**kwargs` returns a dictionary (with the keyword as the key and the value as the value)
- For example, if we pass `add=3` and `multiply=2` to the function, `**kwargs` will return `{'add': 3, 'multiply': 2}`.

```python
# main.py

def calculate(n, **kwargs):
    print(kwargs) # {'add': 3, 'multiply': 2}
    for key, value in kwargs.items():
        print(key) # add
                   # multiply
        print(value) # 3
                     # 2
    n += kwargs["add"]
    n *= kwargs["multiply"]
    print(n) # 15

calculate(2, add=3, multiply=2) # 15
```

- `*args` and `**kwargs` are just conventions and we can use any name we want.

```python
# main.py

# *args
def add(*numbers):
    total = 0
    for n in numbers:
        total += n
    return total

print(add(1, 2, 3, 4, 5)) # 15

# **kwargs

def calculate(n, **operations):
    print(operations) # {'add': 3, 'multiply': 2}
    for key, value in operations.items():
        print(key) # add
                   # multiply
        print(value) # 3
                     # 2
    n += operations["add"]
    n *= operations["multiply"]
    print(n) # 15

calculate(2, add=3, multiply=2) # 15
```

- `*args` collects positional arguments as a tuple.

### Creating a class with optional arguments

```python
# main.py

class Car:
    def __init__(self, **kw):
        self.make = kw.get("make")
        self.model = kw.get("model")

my_car = Car(make="Nissan", model="GT-R")
print(my_car.make) # Nissan
print(my_car.model) # GT-R

```

- The `get()` method returns the value of the item with the specified key or none if the key does not exist.
- This ensures that the program does not crash if the key does not exist.

### Creating a class with default arguments

```python
# main.py

class Car:
    def __init__(self, make="Nissan", model="GT-R"):
        self.make = make
        self.model = model

        my_car = Car()
        print(my_car.make) # Nissan
        print(my_car.model) # GT-R


```

## GUI in python with tkinter

### tkinter

- tkinter is a python library that is used to create GUI applications.
- tkinter is a built-in library and therefore we do not need to install it.
- tkinter is a cross-platform library and therefore it works on Windows, Mac and Linux.
- tkinter is a wrapper around the Tk GUI toolkit.

### Tk GUI toolkit

- Tk is a GUI toolkit that is used to create GUI applications.

### Creating a window

```python
# main.py
from tkinter import *

window = Tk()
window.title("My First GUI Program")
window.minsize(width=500, height=300)

# Label
my_label = Label(text="I am a Label", font=("Arial", 24, "bold"))
my_label.pack()

# Button
def button_clicked():
    my_label.config(text="Button got clicked")

button = Button(text="Click Me", command=button_clicked)
button.pack()

window.mainloop() # keep the window on the screen
```

- The `Label` widget is used to display text on the screen.
- The `Button` widget is used to create a button.
- The `command` parameter is used to specify the function that will be called when the button is clicked.
- The `pack()` method is used to display the widget on the screen.
- The `mainloop()` method is used to keep the window on the screen.
- The `config()` method is used to change the text of the label.

### Other widgets

- `Entry` widget: used to create a text entry box.
- `Text` widget: used to create a multi-line text entry box.
- `Spinbox` widget: used to create a spinbox.
- `Scale` widget: used to create a scale.
- `Checkbutton` widget: used to create a checkbutton.
- `Radiobutton` widget: used to create a radiobutton.
- `Listbox` widget: used to create a listbox.
- `Frame` widget: used to create a frame.
- `Canvas` widget: used to create a canvas.
- `Menu` widget: used to create a menu.
- `Message` widget: used to create a message.
- `LabelFrame` widget: used to create a label frame.
- `PanedWindow` widget: used to create a paned window.
- `tkMessageBox` widget: used to display message boxes.
- `tkFileDialog` widget: used to open and save files.

```python
# main.py
from tkinter import *

window = Tk()
window.title("My First GUI Program")
window.minsize(width=500, height=300)

# Label
my_label = Label(text="I am a Label", font=("Arial", 24, "bold"))
my_label.pack()

# Button
def button_clicked():
    my_label.config(text="Button got clicked")

button = Button(text="Click Me", command=button_clicked)
button.pack()

# Entry
input = Entry(width=10)
input.pack()

# Text
text = Text(height=5, width=30)
text.pack()

# Spinbox
def spinbox_used():
    print(spinbox.get())

spinbox = Spinbox(from_=0, to=10, width=5, command=spinbox_used)
spinbox.pack()

# Scale
def scale_used(value):
    print(value)

scale = Scale(from_=0, to=100, command=scale_used)
scale.pack()

# Checkbutton
def checkbutton_used():
    print(checked_state.get())

checked_state = IntVar()
checkbutton = Checkbutton(text="Is On?", variable=checked_state, command=checkbutton_used)
checked_state.get()
checkbutton.pack()

# Radiobutton
def radio_used():
    print(radio_state.get())

radio_state = IntVar()
radiobutton1 = Radiobutton(text="Option1", value=1, variable=radio_state, command=radio_used)
radiobutton2 = Radiobutton(text="Option2", value=2, variable=radio_state, command=radio_used)
radiobutton1.pack()
radiobutton2.pack()

# Listbox
def listbox_used(event):
    print(listbox.get(listbox.curselection()))

listbox = Listbox(height=4)
fruits = ["Apple", "Pear", "Orange", "Banana"]
for item in fruits:
    listbox.insert(fruits.index(item), item)
listbox.bind("<<ListboxSelect>>", listbox_used)
listbox.pack()

# Frame
frame = Frame(height=100, width=100)
frame.pack()

# Canvas
canvas = Canvas(height=100, width=100)
canvas.pack()

# Menu
def menu_used():
    print("Menu item clicked")

menu = Menu()
menu.add_command(label="Item 1", command=menu_used)
menu.add_command(label="Item 2", command=menu_used)
menu.add_command(label="Item 3", command=menu_used)
menu.add_command(label="Item 4", command=menu_used)
menu.add_command(label="Item 5", command=menu_used)
menu.add_command(label="Item 6", command=menu_used)
menu.add_command(label="Item 7", command=menu_used)
menu.add_command(label="Item 8", command=menu_used)

window.config(menu=menu)

# Message
message = Message(text="This is a message")
message.pack()

# LabelFrame
labelframe = LabelFrame(text="This is a label frame")
labelframe.pack()

# PanedWindow
panedwindow = PanedWindow(orient=VERTICAL)
panedwindow.pack(fill=BOTH, expand=True)

label1 = Label(panedwindow, text="Label1")
label1.pack()

panedwindow.add(label1)

label2 = Label(panedwindow, text="Label2")
panedwindow.add(label2)


window.mainloop() # keep the window on the screen
```

- More information about tkinter can be found [in the python docs using this link](https://docs.python.org/3/library/tkinter.html).

## Pack, Grid and Place

`Pack`, `Grid` and `Place` are the three layout managers in tkinter.

### Pack

- The `pack()` method is used to display the widget on the screen.
- It packs the widgets in a block. Either horizontally or vertically.
- It is the easiest to use but it is not the most precise.

### Place

- The `place()` method is used to display the widget on the screen.
- It packs the widgets in a specific position using x and y coordinates.
- It is the most precise but it is not the easiest to use.
- It is not responsive.

```python
 label.place(x=0, y=0)
```

### Grid

- The `grid()` method is used to display the widget on the screen.
- It packs the widgets in a grid of rows and columns.
- It is the best to use.
- It is responsive.

```python
label.grid(column=0, row=0) # label will be placed in the first column and the first row

label.grid(column=1, row=0) # label will be placed in the second column and the first row
```

- The `columnspan` parameter is used to specify the number of columns the widget will span.
- The `rowspan` parameter is used to specify the number of rows the widget will span.

```python
label.grid(column=0, row=0, columnspan=2) # label will be placed in the first column and the first row and will span two columns

label.grid(column=0, row=0, rowspan=2) # label will be placed in the first column and the first row and will span two rows
```

{: .prompt-warning}

> - When we use the `grid()` method, we do not need to use the `pack()` method.
> - They are incompatible with each other.

### Padding

- The `padx` parameter is used to specify the padding on the left and right of the widget.
- The `pady` parameter is used to specify the padding on the top and bottom of the widget.

```python
label.config(padx=10, pady=10)
```

### Mile to Km converter

```python

from tkinter import *


def miles_kilometers():
    miles = float(text_input.get())
    km = miles * 1.609
    km_result_label.config(text=f"{km}")
    # user_input = text_input.get()
    # km_result_label.config(text=user_input)
    # km_result_label.config(text=float(user_input) * 1.609)


window = Tk()
window.title("Mile to Km Converter")

window.minsize(width=300, height=100)
window.config(padx=20, pady=20)

# Label
equals_label = Label(text="is equal to", font=("Arial", 24, "bold"))
equals_label.grid(column=0, row=1)

# Label
km_result_label = Label(text="0", font=("Arial", 24, "bold"))
km_result_label.grid(column=1, row=1)

# Label
miles_label = Label(text="Miles", font=("Arial", 24, "bold"))
miles_label.grid(column=2, row=0)

# Label
kilometer_label = Label(text="Km", font=("Arial", 24, "bold"))
kilometer_label.grid(column=2, row=1)

# Entry
text_input = Entry(width=10)
text_input.grid(column=1, row=0)

# Button


button = Button(text="Calculate", command=miles_kilometers)
button.grid(column=1, row=2)

window.mainloop()

```
