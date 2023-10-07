---
layout: post
title: 100 Days Of Python - Day 37
date: 2023-10-06 06:21 +0000
categories: [Python Tutorial, Day 37]
tags: [day 37, html, render_template]
---

## Day 37

## Rendering HTML from a file

- We can render HTML from a file using the `render_template` function from flask
- We need to create a `templates` folder in the same directory as our `main.py` file
- We can then create an HTML file in the `templates` folder
- We can then use the `render_template` function to render the HTML file

```python
from flask import Flask, render_template

app = Flask(__name__)


@app.route("/")
def home():
    return render_template("index.html")


if __name__ == "__main__":
    app.run(debug=True)
```
