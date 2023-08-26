---
layout: post
title: 100 Days Of Python - Day 15
date: 2023-08-20 11:06 +0000
categories: [Python Tutorial, Day 15]
tags: [day 15, installing python on ubuntu, installing pycharm on ubuntu]
---

## Day 15

## Setting up a local development environment

- Installing Python on Ubuntu 22.04 using the terminal

```bash
sudo apt update
sudo apt-get install python3 python3-dev
```

**Source:** [How to Install Python 3.9 on Ubuntu 20.04](https://wiki.python.org/moin/BeginnersGuide/Download)

- Installing Pycharm on Ubuntu 22.04 using the terminal

```bash
sudo snap install pycharm-community --classic
```

**Source:** [Install PyCharm on Ubuntu using the Snap Store](https://www.jetbrains.com/help/pycharm/installation-guide.html#ccb90a48)

## Coffee Machine

{: .prompt-info}

> ### Instructions
>
> Congratulations, you've got a job at Python Loves Coffee, a new coffee shop that's just opened up in town! Because Python loves coffee, you have to write a program that will work out the total cost of an order for coffee.
>
> ### Example Input
>
> ```
> What would you like? (espresso/latte/cappuccino): latte
>
> How many shots? (1 or 2): 2
>
> Would you like a shot of hazelnut? (y/n): y
>
> Would you like a shot of vanilla? (y/n): n
>
> How many sugars? (0, 1, 2, 3, 4): 2
> ```
>
> ### Example Output
>
> ```
> That will be $2.50 please.
> ```

{: .prompt-tip}

> ### Hint
>
> 1. Think about what coffee types and extras you have and how much they cost.
> 2. Check the data type of the different inputs you receive. If you want to use the test code below, `you can print(type(variable_name))` to see the type of variable you're working with.
> 3. The `test` code contains `pass`. This is a keyword that does nothing at all. It's just a placeholder for where you might want to add some code in the future.
> 4. If you want to use the test code, remember to indent all of your code after `if __name__ == "__main__":`

### Test Code

```python
if __name__ == "__main__":


    def test(coffee_type, shots, hazelnut, vanilla, sugar, expected):
        print(f"Testing {coffee_type} with {shots} shots, hazelnut={hazelnut}, vanilla={vanilla}, {sugar} sugars.")
        actual = coffee_machine(coffee_type, shots, hazelnut, vanilla, sugar)
        if actual == expected:
            print("Pass")
        else:
            print(f"Fail! Expected {expected}, but got {actual}")
        print()


    # Parameters: coffee_type, shots, hazelnut, vanilla, sugar
    test("espresso", 1, False, False, 0, 1.50)
    test("latte", 2, True, False, 2, 3.50)
    test("cappuccino", 1, False, True, 1, 3.00)
```

### Solution

```python
MENU = {
    "espresso": {
        "ingredients": {
            "water": 50,
            "coffee": 18,
        },
        "cost": 1.5,
    },
    "latte": {
        "ingredients": {
            "water": 200,
            "milk": 150,
            "coffee": 24,
        },
        "cost": 2.5,
    },
    "cappuccino": {
        "ingredients": {
            "water": 250,
            "milk": 100,
            "coffee": 24,
        },
        "cost": 3.0,
    }
}

profit = 0
resources = {
    "water": 300,
    "milk": 200,
    "coffee": 100,
}


def is_resource_sufficient(order_ingredients):
    """Returns True when order can be made, False if ingredients are insufficient."""
    for item in order_ingredients:
        if order_ingredients[item] > resources[item]:
            print(f"​Sorry there is not enough {item}.")
            return False
    return True


def process_coins():
    """Returns the total calculated from coins inserted."""
    print("Please insert coins.")
    total = int(input("how many quarters?: ")) * 0.25
    total += int(input("how many dimes?: ")) * 0.1
    total += int(input("how many nickles?: ")) * 0.05
    total += int(input("how many pennies?: ")) * 0.01
    return total


def is_transaction_successful(money_received, drink_cost):
    """Return True when the payment is accepted, or False if money is insufficient."""
    if money_received >= drink_cost:
        change = round(money_received - drink_cost, 2)
        print(f"Here is ${change} in change.")
        global profit
        profit += drink_cost
        return True
    else:
        print("Sorry that's not enough money. Money refunded.")
        return False


def make_coffee(drink_name, order_ingredients):
    """Deduct the required ingredients from the resources."""
    for item in order_ingredients:
        resources[item] -= order_ingredients[item]
    print(f"Here is your {drink_name} ☕️. Enjoy!")


is_on = True

while is_on:
    choice = input("​What would you like? (espresso/latte/cappuccino): ")
    if choice == "off":
        is_on = False
    elif choice == "report":
        print(f"Water: {resources['water']}ml")
        print(f"Milk: {resources['milk']}ml")
        print(f"Coffee: {resources['coffee']}g")
        print(f"Money: ${profit}")
    else:
        drink = MENU[choice]
        if is_resource_sufficient(drink["ingredients"]):
            payment = process_coins()
            if is_transaction_successful(payment, drink["cost"]):
                make_coffee(choice, drink["ingredients"])

```
