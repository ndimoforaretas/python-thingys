---
layout: post
title: 100 Days Of Python - Day 17
date: 2023-08-26 10:15 +0000
categories: [Python Tutorial, Day 17]
tags: [day 17, creating classes, creating objects]
---

## Day 17

## Creating Classes

- Classes are blueprints for creating new objects.
- If the class name is has more than one word, it is written in `PascalCase`.
- The syntax for creating a class is:

```python
class ClassName:
```

- If a class has no methods, it can be created with the `pass` keyword. This is useful when you want to create a class but don't want to add any methods to it yet.

```python

class ClassName:
    pass
```

### Creating Objects

- Objects are instances of a class.
- If the object name is has more than one word, it is written in `snake_case`.
- The syntax for creating an object is:

```python
object_name = ClassName()
```

### Adding Attributes to Objects

- Attributes are variables that belong to an object.
- Attributes are added to an object using the dot notation.
- The syntax for adding an attribute to an object is:

```python
object_name.attribute_name = value

# Example
car.color = "red"
```

### Adding Attributes to Classes

- Attributes can be added to a class using the `__init__()` method.
- The `__init__()` method is called when an object is created.
- It is also called the constructor method.
- The `__init__()` method is used to initialize the attributes of an object.

```python
class ClassName:
    def __init__(self, attribute1, attribute2):
        self.attribute1 = attribute1
        self.attribute2 = attribute2

# Example
class Car:
    def __init__(self, color, mileage):
        self.color = color
        self.mileage = mileage

car = Car("blue", 20000)
print(car.color)
print(car.mileage)

# Output:
# blue
# 20000

```

- The `self` keyword refers to the current object.

```python
class User:
    def __init__(self, user_id, username):
        self.id = user_id
        self.username = username

user_1 = User("001", "Aretas")
print(user_1.id)
print(user_1.username)

# Output:
# 001
# Aretas

```

- defaulf values can be set for attributes in the `__init__()` method.

```python
class User:
    def __init__(self, user_id, username, email):
        self.id = user_id
        self.username = username
        self.email = email
        self.followers = 0
        self.following = 0
```

### Adding Methods to Classes

- Methods are functions that belong to a class.
- Methods are added to a class using the dot notation.
- The syntax for adding a method to a class is:

```python
class ClassName:
    def method_name(self):
        # code goes here

# Example
class Car:
    def __init__(self, color, mileage):
        self.color = color
        self.mileage = mileage

    def drive(self, miles):
        self.mileage += miles

car = Car("blue", 20000)
print(car.mileage)
car.drive(100)
print(car.mileage)

# Output:
# 20000
# 20100

```

- The `self` keyword refers to the current object.

```python
class User:
    def __init__(self, user_id, username, email):
        self.id = user_id
        self.username = username
        self.email = email
        self.followers = 0
        self.following = 0

    def follow(self, user):
        user.followers += 1
        self.following += 1

```
