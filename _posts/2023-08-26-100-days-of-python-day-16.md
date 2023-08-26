---
layout: post
title: 100 Days Of Python - Day 16
date: 2023-08-26 06:13 +0000
categories: [Python Tutorial, Day 16]
tags: [day 16]
---

## Day 16

## Procedural Programming

The code in the previous day (Day 15) is an example of **procedural programming**.
This is a programming paradigm, derived from structured programming, based on the concept of the procedure call.

- Procedures, also known as routines, subroutines, or functions, simply contain a series of computational steps to be carried out.
- Any given procedure might be called at any point during a program's execution, including by other procedures or itself.

## Object Oriented Programming

**Object-oriented programming** (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods).

A feature of objects is that an object's own procedures can access and often modify the data fields of itself (objects have a notion of this or self).

- In OOP, computer programs are designed by making them out of objects that interact with one another.
- OOP languages are diverse, but the most popular ones are class-based, meaning that objects are instances of classes, which also determine their types.

### How to use OOP in Python

- Every object has an attribute and a method.
  - Attributes are like variables that belong to an object.
  - Methods are like functions that belong to an object.

### Classes

- A class is a blueprint for creating new objects.
- A class can contain methods (functions) and attributes (similar to keys in a dictionary).
- Classes are named in PascalCase.

### Objects

- An object is an instance of a class.
- Objects are named in snake_case.
- Objects are created using the `class_name()` syntax.
- Objects can have attributes and methods.

```python
class Car:
    def __init__(self, color, mileage):
        self.color = color
        self.mileage = mileage

    def __str__(self):
        return f"The {self.color} car has {self.mileage} miles."

    def drive(self, miles):
        self.mileage += miles


car = Car("blue", 20000)
print(car)
car.drive(100)
print(car)
```

## Pretty Table

- PrettyTable is a Python library for generating simple ASCII tables. (Check out the Resources category for more info on PrettyTable.)

```python
import prettytable
table = prettytable.PrettyTable()
table.add_column("Pokemon Name", ["Pikachu", "Squirtle", "Charmander"])
table.add_column("Type", ["Electric", "Water", "Fire"])
table.align = "l"
print(table)

# +---------------+----------+
# | Pokemon Name  | Type     |
# +---------------+----------+
# | Pikachu       | Electric |
# | Squirtle      | Water    |
# | Charmander    | Fire     |
# +---------------+----------+

```

### Coffee Machine in OOP

```python
# main.py
from menu import Menu, MenuItem
from coffee_maker import CoffeeMaker
from money_machine import MoneyMachine

money_machine = MoneyMachine()
coffee_maker = CoffeeMaker()
menu = Menu()

is_on = True

while is_on:
    options = menu.get_items()
    choice = input(f"What would you like? ({options}): ")
    if choice == "off":
        is_on = False
    elif choice == "report":
        coffee_maker.report()
        money_machine.report()
    else:
        drink = menu.find_drink(choice)
        if coffee_maker.is_resource_sufficient(drink):
            if money_machine.make_payment(drink.cost):
                coffee_maker.make_coffee(drink)

# menu.py

class Menu:
    def __init__(self):
        self.menu = {
            "espresso": MenuItem("espresso", 50, 0, 18, 1.5),
            "latte": MenuItem("latte", 200, 150, 24, 2.5),
            "cappuccino": MenuItem("cappuccino", 250, 100, 24, 3.0),
        }

    def get_items(self):
        """Returns all the names of the available menu items"""
        options = ""
        for item in self.menu:
            options += f"{item}/"
        return options

    def find_drink(self, order_name):
        """Searches the menu for a particular drink by name. Returns a MenuItem object if it exists, otherwise returns None"""
        if order_name in self.menu:
            return self.menu[order_name]
        else:
            print("Sorry that item is not available.")

# coffee_maker.py

class CoffeeMaker:
    """Models the machine that makes the coffee"""

    def __init__(self):
        self.resources = {
            "water": 300,
            "milk": 200,
            "coffee": 100,
        }

    def report(self):
        """Prints a report of all resources"""
        print(f"Water: {self.resources['water']}ml")
        print(f"Milk: {self.resources['milk']}ml")
        print(f"Coffee: {self.resources['coffee']}g")

    def is_resource_sufficient(self, drink):
        """Returns True when order can be made, False if ingredients are insufficient"""
        can_make = True
        for item in drink.ingredients:
            if drink.ingredients[item] > self.resources[item]:
                print(f"Sorry there is not enough {item}.")
                can_make = False
        return can_make

    def make_coffee(self, order):
        """Deducts the required ingredients from the resources"""
        for item in order.ingredients:
            self.resources[item] -= order.ingredients[item]
        print(f"Here is your {order.name} ☕️. Enjoy!")

# money_machine.py

class MoneyMachine:
    CURRENCY = "£"

    COIN_VALUES = {
        "pennies": 0.01,
        "nickles": 0.05,
        "dimes": 0.1,
        "quarters": 0.25,
        "pounds": 1.0,
    }

    def __init__(self):
        self.profit = 0
        self.money_received = 0

    def report(self):
        """Prints the current profit"""
        print(f"Money: {self.CURRENCY}{self.profit}")

    def process_coins(self):
        """Returns the total calculated from coins inserted"""
        print("Please insert coins.")
        for coin in self.COIN_VALUES:
            self.money_received += int(input(f"How many {coin}?: ")) * self.COIN_VALUES[coin]
        return self.money_received

    def make_payment(self, cost):
        """Returns True when payment is accepted, or False if insufficient"""
        self.process_coins()
        if self.money_received >= cost:
            change = round(self.money_received - cost, 2)
            print(f"Here is {self.CURRENCY}{change} in change.")
            self.profit += cost
            self.money_received = 0
            return True
        else:
            print("Sorry that's not enough money. Money refunded.")
            self.money_received = 0
            return False


```
