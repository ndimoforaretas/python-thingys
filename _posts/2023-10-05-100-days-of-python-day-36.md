---
layout: post
title: 100 Days Of Python - Day 36
date: 2023-10-05 21:56 +0000
categories: [Python Tutorial, Day 36]
tags: [day 36, advanced python decorators, guess the number game]
---

## Day 36

### Running different paths on Flask

- We can run different paths on flask using the `@app.route` decorator

```python
from flask import Flask

app = Flask(__name__)


@app.route("/")
def hello_world():
    return "<h1>Hello, World!</h1>"

@app.route("/about")
def say_bye():
    return "<h1>About Page</h1>"
```

- The first path takes us to the home or root page
- The second path takes us to the about page

### Passing variables to the path

- We can pass variables to the path using the `<variable_name>` syntax
- We can also specify the type of the variable using the `<type:variable_name>` syntax

```python
from flask import Flask

app = Flask(__name__)


@app.route("/")
def hello_world():
    return "<h1>Hello, World!</h1>"

@app.route("/about")
def say_bye():
    return "<h1>About Page</h1>"

@app.route("/<name>")
def greet(name):
    return f"<h1>Hello, {name}!</h1>"

@app.route("/blog/<int:blog_id>")
def show_blog(blog_id):
    return f"<h1>Blog Number {blog_id}</h1>"
```

- The first path takes us to the home or root page
- The second path takes us to the about page
- The third path takes us to the greet page which greets us with the name we pass to the path
- The fourth path takes us to the blog page which shows the blog number we pass to the path

### Running the flask app in debug mode

- We can run the flask app in debug mode using the `debug=True` argument in the `app.run()` method

```python
from flask import Flask

app = Flask(__name__)


@app.route("/")
def hello_world():
    return "<h1>Hello, World!</h1>"

@app.route("/about")
def about():
    return "<h1>About Page</h1>"

if __name__ == "__main__":
    app.run(debug=True)

```

- the `debug=True` argument in the `app.run()` method will allow us to:
  - see the errors in the browser
  - automatically restart the server when we make changes to the code
  - show a debugger in the browser

## Rendering HTML Templates

- We can render HTML templates using the `render_template()` method from the `flask` module
- We can create a `templates` folder in the root directory of our project and add our HTML templates to it
- We can then use the `render_template()` method to render the HTML templates

```python
from flask import Flask, render_template

app = Flask(__name__)


@app.route("/")
def hello_world():
    return "<h1>Hello, World!</h1>"

@app.route("/about")
def about():
    return render_template("about.html")

if __name__ == "__main__":
    app.run(debug=True)

```

## Advanced Python Decorators

- We can use the `@app.route` decorator to run different paths on flask
- We can also create our own decorators
- We can create a decorator using the following syntax

```python
def my_decorator(function):
    # do something
    return function
```

- We can then use the decorator as follows

```python
@my_decorator
def my_function():
    # do something
    return something
```

- We can also pass arguments to the decorator as follows

```python
def my_decorator(function):
    # do something
    return function

@my_decorator(argument)
def my_function():
    # do something
    return something
```

{:.prompt-info}

> - In the following example, we will create a class that contains a name and a is_logged_in attribute
> - We will then create a decorator that checks if the user is logged in
> - If the user is logged in, we will print the name of the user
> - If the user is not logged in, we will print "Please log in"

```python
class User:
    def __init__(self, name):
        self.name = name
        self.is_logged_in = False

def is_authenticated_decorator(function):
    def wrapper_function(*args, **kwargs):
        if args[0].is_logged_in:
            function(args[0])
        else:
            print("Please log in")
    return wrapper_function

@is_authenticated_decorator
def create_blog_post(user):
    print(f"This is {user.name}'s new blog post.")

new_user = User("John")
create_blog_post(new_user)

# Output:
Please log in

new_user.is_logged_in = True
create_blog_post(new_user)

# Output:
This is John's new blog post.
```

## The guess the number game

{:.prompt-info}

> - In the following example, we will create a guess the number game
> - In the game, the computer will generate a random number between 1 and 10
> - The user will then have to guess the number in the browser path
> - If the user guesses the number correctly, the user will see a "You found me" message and a cat gif
> - If the user guesses the number incorrectly, the user will see a "Try again" message and a different cat gif

{:.prompt-warning}

> ## Instructions
>
> - Create a `server.py` file
>
> 1. Create a new Flask application where the home route displays an <h1> that says "Guess a number between 0 and 9" and display this gif "https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif"
> 2. Generate a random number between 0 and 9
> 3. Create a route that can detect the number entered by the user e.g "URL/3" or "URL/9" and checks that number against the generated random number. If the number is too low, tell the user it's too low, same with too high or if they found the correct number. try to make the <h1> text a different colour for each page. e.g. If the random number was 5:
>    - URL/3 - <h1 style="color:red">Too low, try again!</h1>
>    - URL/5 - <h1 style="color:green">You found me!</h1>
>    - URL/9 - <h1 style="color:red">Too high, try again!</h1>
> 4. Add the gif "https://media.giphy.com/media/4T7e4DmcrP9du/giphy.gif" to the page that displays when the user guesses the correct number
> 5. Add the gif "https://media.giphy.com/media/3o6ZtaO9BZHcOjmErm/giphy.gif" to the page that displays when the user guesses the wrong number

### Solution

```python
from flask import Flask
import random

app = Flask(__name__)

random_number = random.randint(0, 9)

@app.route("/")
def home():
    return "<h1>Guess a number between 0 and 9</h1>" \
           "<img src='https://media.giphy.com/media/3o7aCSPqXE5C6T8tBC/giphy.gif'>"

@app.route("/<int:number>")
def guess(number):
    if number == random_number:
        return "<h1 style='color:green'>You found me!</h1>" \
               "<img src='https://media.giphy.com/media/4T7e4DmcrP9du/giphy.gif'>"

    elif number < random_number:
        return "<h1 style='color:red'>Too low, try again!</h1>" \
               "<img src='https://media.giphy.com/media/3o6ZtaO9BZHcOjmErm/giphy.gif'>"
    else:
        return "<h1 style='color:red'>Too high, try again!</h1>" \
               "<img src='https://media.giphy.com/media/3o6ZtaO9BZHcOjmErm/giphy.gif'>"

if __name__ == "__main__":
    app.run(debug=True)
```
