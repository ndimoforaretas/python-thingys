---
layout: post
title: 100 Days Of Python - Day 38
date: 2023-10-06 19:26 +0000
categories: [Python Tutorial, Day 38]
tags: [day 38, html, render_template]
---

## Day 38

## Templates and Jinja

- We can use the `render_template` function to render HTML from a file
- We can use the `{{ }}` syntax to insert variables into our HTML
- We can use the `{% %}` syntax to add logic to our HTML
- We can use the `for` loop in our HTML to iterate over a list
- We can use the `if` statement in our HTML to add logic to our HTML
- We can use the `with` statement in our HTML to create a variable

```python
from flask import Flask, render_template

app = Flask(__name__)


@app.route("/")
def home():
    return render_template("index.html")


@app.route("/blog")
def blog():
    return render_template("blog.html")


@app.route("/about")
def about():
    return render_template("about.html")

```
