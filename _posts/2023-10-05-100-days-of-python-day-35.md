---
layout: post
title: 100 Days Of Python - Day 35
date: 2023-10-05 20:46 +0000
categories: [Python Tutorial, Day 35]
tags:
  [
    day 35,
    flask,
    web development,
    python functions,
    decorators,
    function run time decorator,
  ]
---

## Day 35

## Web Development with Flask

- Flask is a micro web framework written in Python.
- It is classified as a microframework because it does not require particular tools or libraries.
- It has no database abstraction layer, form validation, or any other components where pre-existing third-party libraries provide common functions.
- However, Flask supports extensions that can add application features as if they were implemented in Flask itself.

### Installation & Setup

- Install flask using pip

```python
pip install flask
```

- Create a new python file called `hello.py`

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<h1>Hello, World!</h1>"
```

- Run the flask app in the terminal using the following command

```bash
flask --app hello run
# output
 * Serving Flask app 'hello'
 * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
```

- The following code can help us use the run or stop button on pycharm to run the flask app

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>"

if __name__ == "__main__":
    app.run()
```

### More on Python Functions

- Functions can have inputs/functionality/output

```python
def add(n1, n2):
    return n1 + n2

def subtract(n1, n2):
    return n1 - n2

def multiply(n1, n2):
    return n1 * n2

def divide(n1, n2):
    return n1 / n2
```

- Functions are first-class objects, can be passed around as arguments e.g. int/string/float etc.

```python
def calculate(calc_function, n1, n2):
    return calc_function(n1, n2)

result = calculate(add, 2, 3)
print(result)
```

- Functions can be nested in other functions

```python
def outer_function():
    print("I'm outer")

    def nested_function():
        print("I'm inner")

    nested_function()

outer_function()
```

- Functions can be returned from other functions

```python
def outer_function():
    print("I'm outer")

    def nested_function():
        print("I'm inner")

    return nested_function

inner_function = outer_function()
inner_function()
```

### Decorators

- Functions that change the behaviour of other functions
- Higher Order Functions (HOC) - A function that either:
  - Accepts a function as a parameter
  - Returns a function
  - Or both
- Syntactic Sugar - A shorthand way to write something

```python
def greet():
    print("Hello")

greet()

# Output
Hello
```

```python
def greet():
    def add():
        return 2 + 3

    return add()

greet()

# Output
5
```

```python
## Simple Python Decorator Functions
import time

def delay_decorator(function):
    def wrapper_function():
        time.sleep(2)
        #Do something before
        function()
        function()
        #Do something after
    return wrapper_function

@delay_decorator
def say_hello():
    print("Hello")

#With the @ syntactic sugar
@delay_decorator
def say_bye():
    print("Bye")

#Without the @ syntactic sugar
def say_greeting():
    print("How are you?")
decorated_function = delay_decorator(say_greeting)
decorated_function()

```

### Function run time decorator

{:.prompt-info}

> - In the following example, we will use a decorator to calculate the run time of a function
> - We will use the `time` module to calculate the run time of a function
> - By using the `time` module, we can calculate the run time of a function by subtracting the start time from the end time

```python
import time

def speed_calc_decorator(function):
    def wrapper_function():
        start_time = time.time()
        function()
        end_time = time.time()
        print(f"{function.__name__} run speed: {end_time - start_time}s")
    return wrapper_function

@speed_calc_decorator
def fast_function():
    for i in range(10000000):
        i * i

@speed_calc_decorator
def slow_function():
    for i in range(100000000):
        i * i

fast_function()
slow_function()
```
