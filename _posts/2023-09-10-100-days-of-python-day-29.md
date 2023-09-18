---
layout: post
title: 100 Days Of Python - Day 29
date: 2023-09-10 04:27 +0000
categories: [Python Tutorial, Day 29]
tags: [day 29, standard dialogs, password generator]
---

## Day 29

## Standard Dialogs

- `Standard Dialogs` are used to get input from the user.
- They are similar to `alerts` and `prompts` in `JavaScript`.
- The `tkinter` module has a number of standard dialogs that you can use.
- These are pop-up windows that appear on top of the current window, and are used to get input from the user or to display information.
- The `tkinter` module has the following standard dialogs −
  - `tkinter.messagebox`
  - `tkinter.filedialog`
  - `tkinter.colorchooser`
  - `tkinter.font`
  - `tkinter.scrolledtext`
  - `tkinter.simpledialog`

### Password Generator

- The `password generator` is a simple program that generates a random password.
- The user inputs a website name, an email/username, and a password.
- The user can also generate a random password which is copied to the clipboard.
- When the user clicks the `Add` button, the website name, email/username, and password are added to a text file which is stored in the same directory as the program.

```python
from tkinter import *
from tkinter import messagebox
from random import choice, randint, shuffle
# ---------------------------- PASSWORD GENERATOR ------------------------------- #
#Password Generator Project
import random
import pyperclip
#Password Generator Project
# def generate_password():
#     #Pass
#     password_entry.delete(0, END)
#     #Password list
#     password_list = []
#     #Letters
#     for char in range(random.randint(8, 10)):
#         password_list.append(chr(random.randint(97, 122)))
#     #Symbols
#     for char in range(random.randint(2, 4)):
#         password_list += chr(random.randint(33, 47))
#     #Numbers
#     for char in range(random.randint(2, 4)):
#         password_list += chr(random.randint(48, 57))
#     #Shuffle
#     random.shuffle(password_list)
#     #Password
#     password = ""
#     for char in password_list:
#         password += char
#     #Output
#     password_entry.insert(0, password)
#     pyperclip.copy(password)
# OR we could use list comprehension
def generate_password():
    letters = ["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z"]
    numbers = ["1", "2", "3", "4", "5", "6", "7", "8", "9"]
    symbols = ["!", "#", "$", "%", "&", "(", ")", "*", "+"]
    password_letters = [choice(letters) for _ in range(randint(8, 10))]
    password_symbols = [choice(symbols) for _ in range(randint(2, 4))]
    password_numbers = [choice(numbers) for _ in range(randint(2, 4))]

    password_list = password_letters + password_symbols + password_numbers
    shuffle(password_list)

    password = "".join(password_list)
    password_entry.insert(0, password)

    pyperclip.copy(password)

# ---------------------------- SEARCH PASSWORD ------------------------------- #
# get the data from the entries
# search for the website in the file
# if found, show the email and password
# if not found, show an error message
# def search():
#     website = website_entry.get()
#     try:
#         with open("data.txt") as data_file:
#             for line in data_file:
#                 if website in line:
#                     email, password = line.split(" | ")[1:3]
#                     messagebox.showinfo(title=website, message=f"Email: {email}\nPassword: {password}")
#     except FileNotFoundError:
#         messagebox.showinfo(title="Error", message="No Data File Found")
#     except ValueError:
#         messagebox.showinfo(title="Error", message="No details for the website exists")



# ---------------------------- SAVE PASSWORD ------------------------------- #
# get the data from the entries
# create a dictionary
# add the data to the dictionary
# clear the entries
# save the data to a file

def save():
    website = website_entry.get()
    email = email_entry.get()
    password = password_entry.get()
    if len(website) == 0 or len(password) == 0:
        messagebox.showinfo(title="Oops", message="Please don't leave any fields empty")
    else:
        is_ok = messagebox.askokcancel(title=website, message=f"These are the details entered: \nEmail: {email}\n"
                                                              f"Password: {password}\nIs it ok to save?")
        if is_ok:
            with open("data.txt", "a") as data_file:
                data_file.write(f"{website} | {email} | {password}\n")
                website_entry.delete(0, END)
                password_entry.delete(0, END)


# ---------------------------- UI SETUP ------------------------------- #
window = Tk()
window.title("Password Manager")
window.config(padx=50, pady=50)

canvas = Canvas(width=200, height=200)
logo_img = PhotoImage(file="logo.png")
canvas.create_image(100, 100, image=logo_img)
canvas.grid(row=0, column=1)

# Labels
website_label = Label(text="Website:")
website_label.grid(row=1, column=0)
email_label = Label(text="Email/Username:")
email_label.grid(row=2, column=0)
password_label = Label(text="Password:")
password_label.grid(row=3, column=0)

# Entries

# wesite
website_entry = Entry(width=44)
website_entry.grid(row=1, column=1, columnspan=2)
website_entry.focus()# Cursor starts here

# email
email_entry = Entry(width=44)
email_entry.grid(row=2, column=1, columnspan=2)
email_entry.insert(0, "johndoe@gmail.com")# Default value

# password
password_entry = Entry(width=24)
password_entry.grid(row=3, column=1)

# Buttons
generate_password_button = Button(text="Generate Password", command=generate_password)
generate_password_button.grid(row=3, column=2)
add_button = Button(text="Add", width=41, command=save)
add_button.grid(row=4, column=1, columnspan=2)


window.mainloop()
```
