---
layout: post
title: 100 Days Of Python - Day 37
date: 2023-10-03 06:26 +0000
categories: [Python Tutorial, Day 37]
tags: [day 37, selenium, web automation, cookie clicker]
---

## Day 37

## Automating Chrome Browser with Selenium

- Selenium is a portable framework for testing web applications.
- It is open-source software released under the Apache License 2.0.
- With selenium, we can automate the browser to do the repetitive tasks such as filling forms, clicking buttons, etc.

### Installation & Setup

- Install selenium using pip

```python
pip install selenium
```

- Install Chrome Browser

### Working with Selenium

- Import the selenium webdriver

```python
from selenium import webdriver
```

- Create a webdriver object

```python
driver = webdriver.Chrome()
```

- Open a website

```python
driver.get("https://www.google.com")
```

- To keep the chrome browser open, we need to use the chrome options in the webdriver

```python
from selenium import webdriver

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)

# Open a website like amazon.de

driver.get("https://www.amazon.de")

```

- To close a browser tab we can use the following code

```python
driver.close()
```

- To close the entire browser we can use the following code

```python
driver.quit()
```

- With selenium, we can find elements on a website by first importing the By module as followS:

```python
from selenium.webdriver.common.by import By
```

- Then we can use the following methods to find elements on a website:

  - id: `driver.find_element(By.ID, "id")`
  - name: `driver.find_element(By.NAME, "name")`
  - class name: `driver.find_element(By.CLASS_NAME, "class_name")`
  - xpath: `driver.find_element(By.XPATH, "xpath")`

- After selecting an element, we can get the text of the element using the `text` attribute

```python
element = driver.find_element(By.ID, "id")
print(element.text)
```

## Printing the events from python.org

{:.prompt-info}

> - In the following example, we will use selenium to print the events from python.org
> - We will first of all select the element that contains the events and then save the events in a dictionary

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()

driver.get("https://www.python.org")

events_times = driver.find_elements(By.CSS_SELECTOR, ".event-widget time")
events_names = driver.find_elements(By.CSS_SELECTOR, ".event-widget li a")

events = {}

for n in range(len(events_times)):
    events[n] = {
        "time": events_times[n].text,
        "name": events_names[n].text,
    }

print(events)

driver.quit()

# Output as of 05.10.2023

{0: {'time': '2023-10-06', 'name': 'Django Day Copenhagen 2023'}, 1: {'time': '2023-10-06', 'name': 'PyCon ES Canarias 2023'}, 2: {'time': '2023-10-07', 'name': 'DjangoCongress JP 2023'}, 3: {'time': '2023-10-08', 'name': 'TOUFU - Parent-Child Python Programming Workshop'}, 4: {'time': '2023-10-09', 'name': 'PyHEP 2023'}}
```

### Clicking a button

- To click a button we can use the `click()` method

```python
button = driver.find_element(By.ID, "id")
button.click()
```

### Wikipedia main page

{:.prompt-info}

> In the following example, we will use selenium to click on the article count button on the wikipedia main page.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
# get the wikipedia main page
driver.get("https://en.wikipedia.org/wiki/Main_Page")
# get the article count using the css class selector
article_count = driver.find_element(By.CSS_SELECTOR, "#articlecount a")
# click on the article count link
article_count.click()
```

{:.prompt-info}

> - In the following example, we will use selenium to:
>   - find an element using the link text
>   - then click on the link

```python

from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
# get the wikipedia main page
driver.get("https://en.wikipedia.org/wiki/Main_Page")
# get the english link using the link text
english_link = driver.find_element(By.LINK_TEXT, "English")
# click on the all portals link
english_link.click()
```

{:.prompt-info}

> - In the following example, we will use selenium to:
> - find the search box using the name attribute
> - then type in the search box
> - then press the enter key

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
# get the wikipedia main page
driver.get("https://en.wikipedia.org/wiki/Main_Page")
# get the search box using the name attribute
search_box = driver.find_element(By.NAME, "search")
# type in the search box
search_box.send_keys("Python")
# press the enter key
search_box.send_keys(Keys.ENTER)

```

{:.prompt-info}

> - In the following example, we will use selenium to:
>   - fill in a form with our first name, last name and email address

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()

driver.get("http://secure-retreat-92358.herokuapp.com/")
first_name = driver.find_element(By.NAME, "fName")
first_name.send_keys("John")
last_name = driver.find_element(By.NAME, "lName")
last_name.send_keys("Doe")
email = driver.find_element(By.NAME, "email")
email.send_keys("johndoe@email.com")
submit = driver.find_element(By.CSS_SELECTOR, "form button")
submit.click()
```

## The Cookie Clicker Game

{:.prompt-info}

> - In the following example, we will use selenium to:
> - open the cookie clicker game
> - then click on the cookie
> - then click on the upgrades
> - the game will run for 5 minutes

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)

driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()

driver.get("https://orteil.dashnet.org/experiments/cookie/")
driver.implicitly_wait(5)

cookie = driver.find_element(By.ID, "cookie")

# get upgrade item ids
items = driver.find_elements(By.CSS_SELECTOR, "#store div")
item_ids = [item.get_attribute("id") for item in items]

timeout = time.time() + 5
five_min = time.time() + 60 * 5

while True:
    cookie.click()

    # every 5 seconds
    if time.time() > timeout:
        # get all upgrade <b> tags
        all_prices = driver.find_elements(By.CSS_SELECTOR, "#store b")
        item_prices = []

        # convert <b> text into an integer price
        for price in all_prices:
            element_text = price.text
            if element_text != "":
                cost = int(element_text.split("-")[1].strip().replace(",", ""))
                item_prices.append(cost)

        # create dictionary of store items and prices
        cookie_upgrades = {}
        for n in range(len(item_prices)):
            cookie_upgrades[item_prices[n]] = item_ids[n]

        # get current cookie count
        money_element = driver.find_element(By.ID, "money").text
        if "," in money_element:
            money_element = money_element.replace(",", "")
        cookie_count = int(money_element)

        # find upgrades that we can currently afford
        affordable_upgrades = {}
        for cost, id in cookie_upgrades.items():
            if cookie_count > cost:
                affordable_upgrades[cost] = id

        # purchase the most expensive affordable upgrade
        highest_price_affordable_upgrade = max(affordable_upgrades)
        print(highest_price_affordable_upgrade)
        to_purchase_id = affordable_upgrades[highest_price_affordable_upgrade]

        driver.find_element(By.ID, to_purchase_id).click()

        # add another 5 seconds until the next check
        timeout = time.time() + 5

    # after 5 minutes stop the bot and check the cookies per second count
    if time.time() > five_min:
        cookie_per_s = driver.find_element(By.ID, "cps").text
        print(cookie_per_s)
        break
```
