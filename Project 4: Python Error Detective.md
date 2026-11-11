## Project 4: Python Error Detective

### Overview

Unlike the first three projects, where the goal was to write working code from the start, this project focused on something every programmer, system administrator, and IT Support professional does regularly: **troubleshooting**.

Writing code is only half the job. The other half is understanding why code fails and knowing how to fix it. Even experienced developers hit errors every day. What separates them from beginners is the ability to read an error message, find the root cause, and fix it methodically.

So I deliberately created several Python programs with common mistakes. After writing each one, I ran it as if I had inherited a broken script from a colleague, or as if a user had asked me why their automation wasn’t working. Instead of guessing, I:

1. Read the **traceback** (the error report Python prints) carefully.
2. Identified the **error type**.
3. Worked out what the interpreter was trying to tell me.
4. Corrected the code.

I created a **separate Python file for each error**, which let me compare the broken version with the fixed version later.

### Task 1: Understanding a `SyntaxError`

A `SyntaxError` happens when Python can’t even start running the program because the code’s structure breaks Python’s grammar rules. Before running a single line, Python checks that the whole program is valid. If it finds a structural mistake, execution stops immediately.

I created a file named:

```
error_task1.py
```

and deliberately left out the closing parenthesis of a `print` statement:

```python
print("Welcome to Python"
```

I saved and ran it. Python displayed an error similar to:

```
SyntaxError: '(' was never closed
```

The message clearly describes the problem. Python found an opening parenthesis but reached the end without finding the matching closing one. I fixed it by adding the missing parenthesis:

```python
print("Welcome to Python")
```

Running the corrected program produced:

```
Welcome to Python
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/f7f3652a-aae3-4ab2-899b-9bae78ff473e" />
 The terminal with the `SyntaxError: '(' was never closed` message for `error_task1.py`, and then the corrected run printing `Welcome to Python`.
> 

> [!TIP]
When Python reports a `SyntaxError`, the real mistake is usually very close to the line it points to. Missing quotation marks, brackets, parentheses, colons, or incorrect indentation are among the most common causes.
> 

### Task 2: Understanding a `NameError`

A `NameError` happens when Python is asked to use a variable that doesn’t exist. I created:

```
error_task2.py
```

and wrote:

```python
print(username)
```

When I ran it, Python displayed:

```
NameError: name 'username' is not defined
```

Python searched its memory for a variable called `username`, but none had ever been created. Variables don’t exist just because we write their names. A variable must be given a value before it can be used. I corrected the program by defining it first:

```python
username = "Clinton"

print(username)
```

The corrected program produced:

```
Clinton
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/7a067f9f-5b27-4bf6-882b-86d50737ded7" />
The `NameError: name 'username' is not defined` message for `error_task2.py`, then the corrected output `Clinton`.
 

Whenever I see a `NameError` now, one of the first things I check is whether I misspelled a variable name or forgot to define it.

### Task 3: Understanding a `TypeError`

Python stores different kinds of information as different **data types**:

- Text is stored as a string (`str`)
- Whole numbers are stored as integers (`int`)
- Decimal numbers are stored as floats

Sometimes different data types can’t be combined directly. I created:

```
error_task3.py
```

and wrote:

```python
age = 22

print("Age: " + age)
```

Running it produced:

```
TypeError: can only concatenate str (not "int") to str
```

Python was telling me it knows how to join a string to another string, but not a string to an integer. Unlike some languages that convert automatically, Python expects the programmer to be explicit. I fixed it using the `str()` function:

```python
age = 22

print("Age: " + str(age))
```

The corrected output was:

```
Age: 22
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/8480d24a-d7e2-4d87-a4af-08e0e006d11a" />
The `TypeError: can only concatenate str (not "int") to str` message for `error_task3.py`, then the corrected output `Age: 22`.
> 

This task showed me why type conversion functions like `str()`, `int()`, and `float()` are used so often in Python.

### Task 4: Understanding a `ValueError`

A `ValueError` happens when Python receives the right **type** of data but a **value** that can’t be used for the operation. I created:

```
error_task4.py
```

and wrote:

```python
number = int("Python")

print(number)
```

When I ran it, Python displayed:

```
ValueError: invalid literal for int() with base 10: 'Python'
```

The `int()` function expects a string that represents a whole number, such as:

```
"5"
```

or:

```
"100"
```

The word `Python` contains letters, not digits, so Python has no way to turn it into an integer. I replaced it with a valid numeric string:

```python
number = int("100")

print(number)
```

The corrected version produced:

```
100
```

> **📸 Screenshot Placeholder**
Insert screenshot showing: The `ValueError: invalid literal for int() with base 10: 'Python'` message for `error_task4.py`, then the corrected output `100`.
> 

This is why input validation matters. When users enter information, programs should check that the data matches what is expected before trying to process it. (It is also the same `ValueError` I handled in Project 3.)

### Task 5: Understanding a `ZeroDivisionError`

In mathematics, dividing by zero is undefined, and Python follows that rule. I created:

```
error_task5.py
```

and wrote:

```python
print(100 / 0)
```

Running it produced:

```
ZeroDivisionError: division by zero
```

Python stopped immediately because the calculation could not be completed. I fixed it by using a valid divisor:

```python
print(100 / 5)
```

The corrected output was:

```
20.0
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/ccc61d4d-7c92-402b-b782-09717b5ee328" />
The `ZeroDivisionError: division by zero` message for `error_task5.py`, then the corrected output `20.0`.


Whenever a program does calculations, it should make sure the divisor isn’t zero before dividing. This kind of defensive programming prevents runtime failures. I put it into practice in the bonus calculator below.

### Task 6: Solving Multiple Errors in One Program

After understanding each error on its own, I wanted a more realistic scenario. In real IT environments, software rarely has just one mistake, and fixing one error often exposes the next. I created:

```
error_task6.py
```

and deliberately put several problems in it:

```python
name = Clinton

age = "25"

print("My name is " + name)

print(age + 5)
```

**First run.** Python immediately displayed:

```
NameError
```

The reason: `Clinton` without quotation marks is read as a **variable name**, not as text. No variable called `Clinton` existed, so Python raised a `NameError`. I corrected it first:

```python
name = "Clinton"
```

**Second run.** This time Python got further before hitting a completely different error. The line:

```python
print(age + 5)
```

tried to add an integer to a string. Because:

```python
age = "25"
```

stored the value as **text**, Python raised a `TypeError`. I fixed it by storing `age` as an integer:

```python
name = "Clinton"

age = 25

print("My name is " + name)

print(age + 5)
```

The corrected program produced:

```
My name is Clinton
30
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/29bbab42-8b57-47ac-a95c-849238046f26" />
The first run of `error_task6.py` with the `NameError`, the second run showing the `TypeError`, and the final corrected output (`My name is Clinton` and `30`).


> [!IMPORTANT]
This is how debugging works in real life. Fixing the first error often reveals another one that was hidden because execution never reached that part of the program. I learned to correct **one problem at a time**, rerun the program, observe the next error, and repeat until everything works.
> 

### Task 7: Creating My Own Error Scenarios

After the guided exercises, I wanted to prove I really understood them. Instead of following examples, I wrote my own broken programs from scratch. For each of the five major error types, I:

1. Deliberately introduced a mistake.
2. **Predicted** which error Python would produce.
3. Ran the program to check my prediction.
4. Fixed the issue.

The error types I practised were `SyntaxError`, `NameError`, `TypeError`, `ValueError`, and `ZeroDivisionError`. Repeating this several times made me much more comfortable with Python tracebacks. Instead of feeling intimidated by an error message, I started to recognise familiar patterns. Often I could name the error type almost immediately and already knew where to start looking.

### My Troubleshooting Log (Documentation Table)

As I worked through each task I documented the error, its cause, my solution, and the final result. A troubleshooting log like this is a great habit in IT Support. It records what happened, what investigation was done, and how it was resolved. Over time these notes become a personal knowledge base that makes similar problems much faster to solve.

| Task | Error Type | Error Message | Root Cause | Solution | Final Output |
| --- | --- | --- | --- | --- | --- |
| 1 | `SyntaxError` | `SyntaxError: '(' was never closed` | I forgot to close the opening parenthesis in the `print()` statement, so Python could not understand where the statement ended. | Added the missing closing parenthesis `)`. | `Welcome to Python` |
| 2 | `NameError` | `NameError: name 'username' is not defined` | I tried to use a variable that had never been created. Python searched for it in memory but couldn’t find it. | Defined the variable before trying to print it. | `Clinton` |
| 3 | `TypeError` | `TypeError: can only concatenate str (not "int") to str` | I tried to join a string and an integer using the `+` operator. Python does not automatically convert different data types. | Converted the integer to a string using `str(age)`. | `Age: 22` |
| 4 | `ValueError` | `ValueError: invalid literal for int() with base 10` | I tried to convert text (`"Python"`) into an integer, but the string did not contain a valid number. | Replaced the text with a valid numeric string (`"100"`). | `100` |
| 5 | `ZeroDivisionError` | `ZeroDivisionError: division by zero` | The program tried to divide a number by zero, which is mathematically impossible. | Changed the divisor from `0` to `5`. | `20.0` |

Completing this table forced me to slow down and think about each problem instead of immediately searching for an answer online. Rather than simply fixing the code, I identified the error type, understood why it happened, and recorded the steps to solve it. That mirrors the troubleshooting process in IT Support, where documenting the problem and its resolution is just as important as fixing it.

### Root Cause Analysis Pattern I Followed

Every task followed the same workflow, and it is the same one I would use on a real support ticket:

| Stage | What I Did |
| --- | --- |
| 1. Observe | Run the program and read the **whole** error message |
| 2. Identify | Name the error type and the line it points to |
| 3. Diagnose | Work out the root cause, not just the symptom |
| 4. Fix | Change **one** thing |
| 5. Test | Run the program again to confirm the fix worked |
| 6. Document | Record the error, cause, solution, and result |

### Bonus Challenge: Building a Crash-Proof Calculator

To finish the project, I built a small calculator that can divide two numbers **without crashing**. The goal was to put everything I’d learned about exception handling into practice. The calculator asks for two numbers, divides the first by the second, and shows the result. Because users can easily make mistakes, like typing letters instead of numbers or dividing by zero, I wrapped the whole operation in a `try` block and added two `except` blocks to catch the most common errors:

```python
try:
    first = float(input("Enter first number: "))
    second = float(input("Enter second number: "))

    result = first / second

    print(f"Result:{result}")

except ZeroDivisionError:
    print("Error: You cannot divide by zero.")

except ValueError:
    print("Error: Please enter valid numbers.")
```

#### How the Program Works

- The first two lines use `float()` to convert the user’s input into decimal numbers. I used `float()` instead of `int()` so the calculator works with both whole numbers and decimals.
- The program then divides and stores the answer in the `result` variable before printing it.
- Because the calculation is inside a `try` block, Python immediately jumps to the matching `except` block if something goes wrong.

There are two errors the program is designed to handle:

| Exception | When It Happens | What the Program Does |
| --- | --- | --- |
| `ZeroDivisionError` | The second number is zero | Shows a clear message that division by zero is not allowed, with no traceback |
| `ValueError` | The user types something that can’t become a number, such as words or symbols | Tells the user that valid numeric input is required |

#### Test 1: Dividing by Zero

I deliberately entered zero as the second number:

```
Enter first number: 20
Enter second number: 0

Error: You cannot divide by zero.
```

The program behaved exactly as expected. Instead of showing a long traceback and stopping, it caught the exception and printed a short, understandable message.

 <img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/91626462-e05d-4654-a775-f40c146a7411" />
  The terminal with `20` and `0` entered and the message `Error: You cannot divide by zero.`


#### Test 2: Successful Division

Next I entered two valid numbers to confirm normal calculations still work:

```
Enter first number: 20
Enter second number: 5

Result: 4.0
```

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/79e96f88-33aa-4857-829e-992ad57c86a3" />
The terminal with `20` and `5` entered and the output `Result: 4.0`.


### ✅ Verification & Testing: Project 4

**Purpose:** Confirm that each deliberate error produced the predicted message, that each fix resolved it, and that the calculator handles bad input safely.

| Test | Scenario | Expected Result | Actual Result | Status |
| --- | --- | --- | --- | --- |
| Task 1 | Fixed `print("Welcome to Python")` | `Welcome to Python` | `Welcome to Python` | ✅ |
| Task 2 | Defined `username` before printing | `Clinton` | `Clinton` | ✅ |
| Task 3 | Used `str(age)` when joining text | `Age: 22` | `Age: 22` | ✅ |
| Task 4 | Used `int("100")` | `100` | `100` | ✅ |
| Task 5 | Divided `100 / 5` | `20.0` | `20.0` | ✅ |
| Task 6 | Fixed `NameError` first, then `TypeError` | `My name is Clinton` and `30` | `My name is Clinton` and `30` | ✅ |
| Calculator 1 | `20` ÷ `0` | `Error: You cannot divide by zero.` | `Error: You cannot divide by zero.` | ✅ |
| Calculator 2 | `20` ÷ `5` | `Result: 4.0` | `Result: 4.0` | ✅ |

**Outcome:** Every error was reproduced, understood, and fixed, and the calculator handled both a divide-by-zero attempt and a normal calculation correctly.

### What This Project Taught Me

Although this project contained very little working application code, it was one of the most valuable exercises in the whole repository. Debugging is a skill that improves with deliberate practice. I learned how to:

- Read Python tracebacks instead of ignoring them.
- Tell syntax errors and runtime errors apart.
- Understand the causes of `SyntaxError`, `NameError`, `TypeError`, `ValueError`, and `ZeroDivisionError`.
- Find the root cause of a problem instead of guessing.
- Correct one error at a time before moving on to the next.
- Rerun programs after every fix to verify the issue was actually resolved.
- Build a systematic troubleshooting mindset like the one needed in IT Support and Help Desk roles.

This way of thinking goes far beyond Python. Whether I’m fixing a broken script, diagnosing a network problem, or helping a user with a software issue, the principle is the same: carefully observe the symptoms, identify the root cause, make one change at a time, test the result, and repeat until the issue is fully resolved.

The calculator also taught me that good software anticipates mistakes instead of assuming users will always provide perfect input. Many support issues come from users entering something unexpected. Writing programs that detect those situations and respond gracefully is just as important as writing code that works under ideal conditions.
