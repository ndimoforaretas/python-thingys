---
layout: post
title: 100 Days Of Python - Day 33
date: 2023-09-29 06:31 +0000
categories: [Python Tutorial, Day 33]
tags: [day 33, api, requests, kanye west, chuck norris, sunrise sunset]
---

## Day 33

## Application Program Interface (API)

### What is an API?

An API is a set of functions that allows applications to access data and interact with external software components, operating systems, or microservices. To simplify, an API delivers a user response to a system and sends the system's response back to a user.

{:.prompt-info}

> An Applicaiton Programming Interface (API) can also be defined as a set of commands, functions, protocols, and objects that programmers can use to create software or interact with an external system.

## Making API requests with Python

- To make API requests with Python, we need to install the `requests` module. To do that, we can use the `pip` command:

```bash
pip install requests
```

- Once the `requests` module is installed, we can import it into our Python script:

```python
import requests
```

- Now we can make API requests using the `requests` module. For example, we can make a `GET` request to the [Open Trivia Database](https://opentdb.com) API to get a list of trivia questions:

```python
import requests

response = requests.get("https://opentdb.com/api.php?amount=10&category=18&difficulty=easy&type=multiple")

print(response.json())
```

## Kanye West Quotes App

- Let's build a simple app that displays a random Kanye West quote every time we run it. To do that, we can use the [Kanye Rest API](https://kanye.rest) to get a random Kanye West quote:

```python
import requests


def get_quote():
    response = requests.get("https://api.kanye.rest")
    response.raise_for_status()
    data = response.json()
    quote = data["quote"]
    print(quote)


get_quote()
```

- Now let's add a button to our app that allows us to get a new quote every time we click on it:

```python
import requests
from tkinter import *


def get_quote():
    response = requests.get("https://api.kanye.rest")
    response.raise_for_status()
    data = response.json()
    quote = data["quote"]
    canvas.itemconfig(quote_text, text=quote)


window = Tk()
window.title("Kanye Says...")
window.config(padx=50, pady=50)

canvas = Canvas(width=300, height=414)
background_img = PhotoImage(file="background.png")
canvas.create_image(150, 207, image=background_img)
quote_text = canvas.create_text(
    150,
    207,
    text="Click the button to get a Kanye West quote",
    width=250,
    font=("Arial", 20, "bold"),
    fill="white"
)
canvas.grid(row=0, column=0)

kanye_img = PhotoImage(file="kanye.png")
kanye_button = Button(image=kanye_img, highlightthickness=0, command=get_quote)
kanye_button.grid(row=1, column=0)

window.mainloop()
```

## Chuck Norris Jokes App

- Let's build another app that displays a random Chuck Norris joke every time we run it. To do that, we can use the [Chuck Norris API](https://api.chucknorris.io) to get a random Chuck Norris joke:

```python
import requests


def get_joke():
    response = requests.get("https://api.chucknorris.io/jokes/random")
    response.raise_for_status()
    data = response.json()
    joke = data["value"]
    print(joke)


get_joke()
```

## Sunlight App

- Let's build another app that displays the time of sunrise and sunset for a given location. To do that, we can use the [Sunrise Sunset API](https://sunrise-sunset.org/api) to get the time of sunrise and sunset for a given location:

```python
import requests
from datetime import datetime
import smtplib
import time

MY_EMAIL = "johndoe@gmail.com"
MY_PASSWORD = "123456htruezrh"

MY_LAT = 52.680859
MY_LONG = 13.583550

def iss_overhead():
    response = requests.get(url="http://api.open-notify.org/iss-now.json")
    response.raise_for_status()

    data = response.json()

    iss_latitude = float(data["iss_position"]["latitude"])
    iss_longitude = float(data["iss_position"]["longitude"])

    if MY_LAT - 5 <= iss_latitude <= MY_LAT + 5 and MY_LONG - 5 <= iss_longitude <= MY_LONG + 5:
        return True

def is_night():
    parameters = {
        "lat": MY_LAT,
        "lng": MY_LONG,
        "formatted": 0,
    }

    response = requests.get("https://api.sunrise-sunset.org/json", params=parameters)
    response.raise_for_status()

    data = response.json()

    sunrise = int(data["results"]["sunrise"].split("T")[1].split(":")[0])
    sunset = int(data["results"]["sunset"].split("T")[1].split(":")[0])

    time_now = datetime.now()

    if time_now.hour >= sunset or time_now.hour <= sunrise:
        return True

while True:
    time.sleep(60)
    if iss_overhead() and is_night():
        connection = smtplib.SMTP("smtp.gmail.com") # Simple Mail Transfer Protocol
        connection.starttls() # Transport Layer Security
        connection.login(user=MY_EMAIL, password=MY_PASSWORD) # Login to email
        connection.sendmail(
            from_addr=MY_EMAIL,
            to_addrs="ndimaret@gmail.com",
            msg="Subject:Look Up\n\nThe ISS is above you in the sky."
        ) # Send email




print(time_now.hour)
```
