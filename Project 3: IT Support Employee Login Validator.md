## Project 3: IT Support Employee Login Validator

### Overview

This project was inspired by something that happens all the time in IT Support and Help Desk environments: **checking what a user typed before letting them continue**. In many organisations, employees enter an Employee ID when logging into an internal application, raising a support ticket, or reaching company resources. These IDs are usually numeric, and invalid data can cause errors if the application isn’t built to handle it.

My goal was a simple login validator that behaves like a basic Help Desk portal. Instead of assuming the user will always type valid information, I designed it to **expect mistakes**. If someone types letters, symbols, decimal numbers, or anything else invalid, the program shows a helpful message and asks again instead of crashing.

Concepts practised: `while` loops, exception handling with `try` and `except`, input validation, and controlling program flow with `break`.

> [!NOTE]
The mindset behind this project is essential in IT Support: never assume users will always give perfect input, and always build systems that recover gracefully from errors.
> 
### Step 1: Create the Project File

Inside `python-practice` I created a new file named:

```
login_validator.py
```

Descriptive filenames keep each exercise easy to find as my collection of Python programs grows.

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/dfb26c5e-f224-4b0f-9d2d-8d9204dc0c46" />
The Explorer panel with `login_validator.py` added to the `python-practice` folder.
> 

### Step 2: Create a Welcome Banner

Before asking for anything, I wanted the program to feel a bit more professional, like the screen you would see when opening an internal company application. I wrote:

```python
print("==================================")
print("Company IT Help Desk")
print("Employee Login Portal")
print("==================================")
```

When run, the program shows:

```
==================================
Company IT Help Desk
Employee Login Portal
==================================
```

This doesn’t change how the program works, but it improves the user experience. Clear headings and descriptive text make software feel polished and easier to understand. I noticed throughout my IT Support training that even simple applications benefit from presenting information clearly.

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/14acbbea-686e-420e-ba8c-5fa06ce9066a" />
The terminal displaying the Help Desk welcome banner.
 

### Step 3: Build the Login Validation Loop

This was the most important part of the project. I wanted the program to keep asking for an Employee ID until a valid number was entered, and otherwise to explain the problem and let the user try again. I combined three Python features: a `while True` loop, a `try` block, and an `except` block.

```python
while True:
    try:
        employee_id = int(input("Enter your Employee ID: "))

        print("Login Successful!")
        print(f"Employee ID:{employee_id}")
        break

    except ValueError:
        print("Invalid Employee ID.")
        print("Please enter numbers only.")
```

There is a lot going on in these few lines, so here is how it works piece by piece.

**`while True:`** creates an infinite loop. Python keeps running the code inside until it reaches a `break`.

**The input line:**

```python
employee_id = int(input("Enter your Employee ID: "))
```

`input()` always returns text, even when the user types digits. Because I wanted the Employee ID treated as a whole number, I wrapped it in `int()`.

If the user types:

```
12345
```

Python converts it to the integer `12345` and stores it in `employee_id`.

If the user types something like:

```
abc
```

or:

```
hello
```

or:

```
12.5
```

Python **cannot** convert those into integers, so it raises a **`ValueError`**.

**Why `try` / `except` matters here:** Normally an uncaught `ValueError` would stop the program immediately and print a traceback, forcing the user to restart the application. Wrapping the conversion in a `try` block prevents that:

- If the conversion **succeeds**, the program carries on normally.
- If the conversion **fails**, Python jumps straight into the `except ValueError:` block.

Inside the handler I print two clear messages:

```python
print("Invalid Employee ID.")
print("Please enter numbers only.")
```

After those messages, the loop starts another round and asks for another Employee ID. This repeats until the user enters valid numeric input.

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/ba9e0226-b82e-4202-9bb0-ad301d88a751" />
 The `while True` / `try` / `except ValueError` block written in VS Code, with syntax highlighting visible.


### Step 4: Exit the Loop After a Successful Login

Once a valid ID is entered, the program prints a confirmation:

```python
print("Login Successful!")
print(f"Employee ID:{employee_id}")
```

The second line uses an f-string, so Python inserts the value stored in `employee_id` into the output. If the user enters `12345`, the program prints:

```
Employee ID: 12345
```

Straight afterwards I use:

```python
break
```

This tells Python to leave the `while True` loop completely. Without it, the program would keep asking for Employee IDs forever, even after a successful login.

### Step 5: Display a Closing Message

`break` only exits the **loop**, not the whole program. After the loop ends, Python simply carries on with the next line of code. I used that to show a closing message:

```python
print("Thank you for using the IT Help Desk.")
```

### Complete Script

```python
print("==================================")
print("Company IT Help Desk")
print("Employee Login Portal")
print("==================================")

while True:
    try:
        employee_id = int(input("Enter your Employee ID: "))

        print("Login Successful!")
        print(f"Employee ID:{employee_id}")
        break

    except ValueError:
        print("Invalid Employee ID.")
        print("Please enter numbers only.")

print("Thank you for using the IT Help Desk.")
```

### Step 6: Save and Test the Program

I saved the file, opened the integrated terminal in VS Code, and ran:

```
python login_validator.py
```

Rather than testing only a successful login, I deliberately typed several **invalid** values first to prove my exception handling worked. I entered `abc`, and the program replied:

```
Invalid Employee ID.
Please enter numbers only.
```

Then I entered `hello`, and it rejected that too with the same helpful message. Finally I entered `12345`, and the program accepted it. The full session looked like this:

```
==================================
Company IT Help Desk
Employee Login Portal
==================================

Enter your Employee ID: abc
Invalid Employee ID.
Please enter numbers only.

Enter your Employee ID: hello
Invalid Employee ID.
Please enter numbers only.

Enter your Employee ID: 12345
Login Successful!
Employee ID: 12345

Thank you for using the IT Help Desk.
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/1d4719d1-9354-4239-a864-3e1d9eb28703" />
 The full terminal session above: the banner, the rejected `abc` and `hello` entries with their error messages, the accepted `12345`, and the closing message.
> 

### ✅ Verification & Testing: Project 3

**Purpose:** Prove that invalid input never crashes the program and that valid input ends the loop correctly.

| Test | Input | Expected Result | Actual Result | Status |
| --- | --- | --- | --- | --- |
| 1 | `abc` | `Invalid Employee ID.` / `Please enter numbers only.` and prompt again | Error message shown, prompted again | ✅ |
| 2 | `hello` | Same error message and prompt again | Same error message, prompted again | ✅ |
| 3 | `12345` | `Login Successful!`, ID displayed, loop exits, closing message | Login confirmed, loop exited, closing message shown | ✅ |

**Outcome:** The program never crashed and always behaved as intended. That is an important characteristic of reliable software: users make mistakes, and well-designed programs handle them without failing unexpectedly.

### Understanding Why `try` / `except` Is Important

While building this project I learned one of Python’s most useful techniques: **exception handling**.

Many beginners try to prevent errors by checking every possible kind of input before converting it. For example, I could have used:

```python
employee_id.isdigit()
```

before converting the value. That works for simple cases, but it quickly gets complicated because I would need to predict every type of invalid input.

With `try` and `except`, I let Python attempt the conversion and handle a failure only if it happens:

- If the conversion succeeds, the program continues.
- If it fails for any reason, Python automatically hands control to the exception handler.

This follows the Python philosophy of *“it’s easier to ask for forgiveness than permission”* (**EAFP**). The code attempts the operation first and deals with exceptions if they occur. It is shorter, and it is also more robust because it handles many kinds of bad input without extra checks.

### Why This Matters

- **Why I did it this way:** Exception handling keeps the code short while covering many kinds of bad input.
- **What it accomplishes:** The user gets a clear message and another chance, not a crash.
- **Why it matters in production:** Many support issues start because users enter something the developer never expected. IT Support tools, admin utilities, automation scripts, and production applications all rely on this kind of input validation.
- **What could go wrong:** Without `try` / `except`, one typo would stop the whole program with a traceback. Without `break`, the loop would never end.

### What I Learned From This Project

By completing this project I gained practical experience with:

- Using `while True` to repeatedly prompt for input.
- Validating user input before processing it.
- Converting strings into integers using `int()`.
- Handling runtime errors with `try` and `except`.
- Understanding the purpose of the `ValueError` exception.
- Using `break` to exit an infinite loop once valid input is received.
- Displaying dynamic information with f-strings.
- Writing programs that keep running even when users make mistakes.
