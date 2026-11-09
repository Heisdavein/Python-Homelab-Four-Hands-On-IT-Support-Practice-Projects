## 🔐 Project 2: Password Strength Checker
 
### Overview
 
In this project I practised two of Python's most useful looping structures, the **`while` loop** and the **`for` loop**, by combining them in a simple password strength checker.
 
The program keeps asking the user for a password until it meets a set of basic security requirements. If the password is too weak, the program says exactly what is missing and asks again. This continues until a strong password is entered.
 
The requirements are:
 
- At least **8 characters** long
- At least **one uppercase letter**
- At least **one lowercase letter**
- At least **one digit**
Along the way I practised loops, conditional statements, Boolean variables, string methods, and user input validation.
 
### Step 1: Create the Project File
 
I created a new Python file inside `python-practice`. Keeping each project in its own file keeps the code organised and lets me go back to earlier exercises without mixing programs together. I named it:
 
```text
password_checker.py
```
 The Explorer panel with `password_checker.py` created next to `movie_recommendation.py`.
 
### Step 2: Create the Main `while` Loop
 
I didn't want the user to enter one weak password and carry on. The program had to keep asking until every requirement was met. So I used an infinite loop with `while True:`
 
```python
# Keep asking until a strong password is entered
 
while True:
    password = input("Enter a password: ")
```
 
- `input()` pauses the program and waits for a password, which is stored in the variable `password`.
- `while True` means the loop runs **forever** unless I stop it with a `break` statement. That was exactly what I wanted, because I had no idea how many attempts a user would need.
### Step 3: Check the Minimum Password Length
 
Before doing detailed checks, I wanted to reject passwords that are obviously too short. There is no point checking for uppercase letters in a three-character password. I used Python's built-in `len()` function to count the characters:
 
```python
if len(password) < 8:
    print("Too short. Try again.")
    continue
```
 
- `len()` returns the length of the string.
- If there are fewer than eight characters, the program prints a message and runs `continue`.
- `continue` skips the rest of the current loop round and jumps back to the start of the `while` loop, which asks for another password.
**Why it matters:** `continue` keeps the program efficient. There is no reason to run more checks on a password that has already failed the minimum length rule.
 
### Step 4: Create Variables to Track Password Requirements
 
Once I knew a password had at least eight characters, I needed to find out whether it also contained an uppercase letter, a lowercase letter, and a number. I created three Boolean variables (a Boolean is a value that is either `True` or `False`):
 
```python
has_upper = False
has_lower = False
has_digit = False
```
 
Each one starts as `False`. As the program examines the password, a variable switches to `True` when its requirement is found. This keeps the program easy to understand because **each variable represents exactly one password rule**.
 
### Step 5: Examine Every Character Using a `for` Loop
 
Next I had to inspect the password one character at a time, which is exactly what a `for` loop is for:
 
```python
for char in password:
    if char.isupper():
        has_upper = True
 
    if char.islower():
        has_lower = True
 
    if char.isdigit():
        has_digit = True
```
 
The statement:
 
```python
for char in password:
```
 
tells Python to look at the password one character at a time. For each character, three checks run:
 
| Check | What It Tests | What Happens |
| ----- | ------------- | ------------ |
| `char.isupper()` | Is the character an uppercase letter? | `has_upper` becomes `True` |
| `char.islower()` | Is the character a lowercase letter? | `has_lower` becomes `True` |
| `char.isdigit()` | Is the character a number? | `has_digit` becomes `True` |
 
The loop carries on until every character has been inspected. By the time it finishes, the three Boolean variables accurately describe whether the password meets each requirement.
 
### Step 6: Decide Whether the Password Is Strong
 
With all the information collected, I used an `if` / `elif` / `else` structure to decide which message to show:
 
```python
if not has_upper:
    print("Missing an uppercase letter. Try again.")
 
elif not has_lower:
    print("Missing a lowercase letter. Try again.")
 
elif not has_digit:
    print("Missing a digit. Try again.")
 
else:
    print("Strong password accepted!")
    break
```
 
The conditions are checked one after another:
 
- No uppercase letter? The user is told straight away.
- Uppercase is present but lowercase is missing? The second condition shows a different message.
- Digits missing? The third condition explains the problem.
- Only when **all three** Booleans are `True` does the program reach the `else` block, print `Strong password accepted!`, and run `break`, which exits the `while` loop so the program can finish.
### Complete Script
 
```python
# Keep asking until a strong password is entered
 
while True:
    password = input("Enter a password: ")
 
    if len(password) < 8:
        print("Too short. Try again.")
        continue
 
    has_upper = False
    has_lower = False
    has_digit = False
 
    for char in password:
        if char.isupper():
            has_upper = True
 
        if char.islower():
            has_lower = True
 
        if char.isdigit():
            has_digit = True
 
    if not has_upper:
        print("Missing an uppercase letter. Try again.")
 
    elif not has_lower:
        print("Missing a lowercase letter. Try again.")
 
    elif not has_digit:
        print("Missing a digit. Try again.")
 
    else:
        print("Strong password accepted!")
        break
```
 
### Step 7: Save and Test the Program
 
I saved the file, opened the integrated terminal in VS Code, and ran:
 
```text
python password_checker.py
```
 
To make sure every part worked, I tested both weak and strong passwords.
 
#### Test 1: Password missing an uppercase letter
 
Input:
 
```text
password123
```
 
Output:
 
```text
Enter a password: password123
Missing an uppercase letter. Try again.
```
 
The program correctly noticed that the password had lowercase letters and numbers but no uppercase characters.
 
> **📸 Screenshot Placeholder**
> Insert screenshot showing: The terminal after entering `password123`, with the message `Missing an uppercase letter. Try again.`
 
#### Test 2: Password missing a digit
 
Input:
 
```text
Password
```
 
Output:
 
```text
Enter a password: Password
Missing a digit. Try again.
```
 
This confirmed that the digit check works independently of the uppercase and lowercase checks.
 
> **📸 Screenshot Placeholder**
> Insert screenshot showing: The terminal after entering `Password`, with the message `Missing a digit. Try again.`
 
#### Test 3: Strong password
 
Input:
 
```text
Password123!
```
 
Output:
 
```text
Enter a password: Password123!
Strong password accepted!
```
 
This final test showed that the program only accepts a password after every requirement has been met.
 
> **📸 Screenshot Placeholder**
> Insert screenshot showing: The terminal after entering `Password123!`, with the message `Strong password accepted!` and the program exiting.
 
### ✅ Verification & Testing: Project 2
 
**Purpose:** Confirm that each password rule is enforced and that the loop only ends on a valid password.
 
| Test | Input | Rule Being Tested | Expected Result | Actual Result | Status |
| ---- | ----- | ----------------- | --------------- | ------------- | ------ |
| 1 | `password123` | Uppercase letter required | `Missing an uppercase letter. Try again.` | `Missing an uppercase letter. Try again.` | ✅ |
| 2 | `Password` | Digit required | `Missing a digit. Try again.` | `Missing a digit. Try again.` | ✅ |
| 3 | `Password123!` | All requirements met | `Strong password accepted!` | `Strong password accepted!` | ✅ |
 
**Outcome:** The checker rejected both weak passwords with a helpful message and accepted the strong one. Testing several inputs gave me confidence that every branch of my logic works.
 
### Understanding Infinite Loops
 
> [!WARNING]
> A `while True` loop never ends on its own. The only ways out are a `break` statement or stopping the program manually. If I accidentally deleted the `break` from this program, it would keep asking for passwords **forever**, even after a strong one was entered.
 
Because of this, I always make sure there is a clear, reachable path to a `break` whenever I use an infinite loop.
 
### Why This Matters
 
- **Why I did it this way:** Checking length first with `continue` avoids pointless work, and Boolean variables make each rule easy to read and change.
- **What it accomplishes:** The program only accepts passwords that meet my rules, and it tells the user what to fix.
- **Why it matters in production:** Validating input before accepting it is a core principle in IT and security. Weak passwords are a leading cause of account compromises, and many systems enforce password rules in a similar way.
- **What could go wrong:** A missing `break` means an endless loop. A missing length check means short passwords pass the other tests. Forgetting to reset the Booleans at the start of each loop would carry results over from a previous attempt (in my script they are set to `False` inside the loop each time).

 
