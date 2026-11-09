## 🎬 Project 1: Age-Based Movie Recommender
 
### Overview
 
My first project was a simple **Age-Based Movie Recommender**. The program is small, but it introduced some of the most important ideas in Python:
 
- Displaying information with `print()`
- Accepting user input with `input()`
- Storing information in variables
- Converting data types with `int()`
- Making decisions with `if`, `elif`, and `else`
The program asks for the user's name and age, then recommends a movie category. This is the same kind of decision-making used by streaming services, online shops, and mobile apps. They collect information from users and decide what to do with it. Mine is far simpler, but the logic is the same.
 
### Step 1: Create the Project File
 
Inside my `python-practice` folder I right-clicked in the VS Code Explorer panel, selected **New File**, and named it:
 
```text
movie_recommendation.py
```
 
**Why:** Descriptive filenames are a habit I try to keep. A name like `test.py` or `project1.py` tells you nothing, but `movie_recommendation.py` tells you straight away what the program does. The file opened in the editor, ready for code.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/c10c94a8-2d38-4ae2-91e4-da528f0ae8f1" />
 The new `movie_recommendation.py` file in the Explorer panel and open in the editor tab.
 
### Step 2: Display a Welcome Message
 
I wanted the program to greet the user so anyone who runs it immediately knows what it is for. I used Python's `print()` function:
 
```python
# Greet the user
print("Welcome to the Movie Recommender!")
```
 
- `print()` shows text on the screen exactly as it appears between the quotation marks.
- A line starting with `#` is a **comment**. Python ignores comments, but they explain the code to humans. As projects grow, comments make code much easier to understand, for me and for anyone else reading it.
When I ran the program after writing this section, the terminal showed:
 
```text
Welcome to the Movie Recommender!
```
 
It looks like a tiny step, but it confirmed that Python was working and my script was running.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/a0135d29-4444-4e9c-8239-4c66812cb021" />
The terminal displaying `Welcome to the Movie Recommender!` after running the first two lines of the script.
 
### Step 3: Ask the User for Their Name
 
Next I made the program interactive using the `input()` function:
 
```python
# Ask for the user's name
name = input("What is your name? ")
```
 
- `input()` pauses the program and waits for the user to type something.
- Whatever they type is stored in a **variable** called `name`. A variable is a labelled container that holds information while the program is running.
For example, if the user types:
 
```text
Clinton
```
 
then the variable contains:
 
```python
name = "Clinton"
```
 
Giving variables meaningful names makes code easier to understand. Naming this one `name` tells me exactly what it holds. When the user presses Enter, the program moves on to the next line.
 
### Step 4: Ask for the User's Age and Convert It
 
Next, the program needed the user's age. I used `input()` again, but this time I wrapped it in `int()`:
 
```python
# Ask for the user's age and convert it to an integer
age = int(input("How old are you? "))
```
 
**Why this step is so important:** `input()` **always returns text**, even when the user types a number. If the user types:
 
```text
25
```
 
Python actually stores it as the string:
 
```python
"25"
```
 
Text can't be compared by size the way numbers can. The `int()` function converts the text into an integer (a whole number), so the variable becomes:
 
```python
age = 25
```
 
instead of:
 
```python
age = "25"
```
 
Now Python can compare ages using these operators:
 
| Operator | Meaning |
| -------- | ------- |
| `<` | less than |
| `>` | greater than |
| `<=` | less than or equal to |
| `>=` | greater than or equal to |
 
> [!IMPORTANT]
> Without converting the input to an integer, the recommendation logic later in the program would produce an error. Converting input to the right data type is one of the most common tasks in real scripts.
 
### Step 5: Write the Decision-Making Logic
 
With the name and age stored, I built the main feature. Python makes decisions using conditional statements, and I combined `if`, `elif`, and `else`:
 
```python
# Recommend a movie category based on age
if age < 10:
    print(f"Hi {name}! We recommend animated movies like Toy Story or Moana.")
 
elif age >= 10 and age < 18:
    print(f"Hey {name}, you might enjoy teen adventure movies like Harry Potter or Spider-Man.")
 
elif age >= 18 and age < 60:
    print(f"{name}, you might enjoy dramas, thrillers, or action movies.")
 
else:
    print(f"{name}, you may enjoy classics or light comedies.")
```
 
This is the heart of the program. Python checks the conditions **from top to bottom**:
 
- If the age is less than 10, the first condition is true and Python recommends animated films.
- If that is false, Python checks whether the age is between 10 and 17.
- If that is also false, Python checks whether the age is between 18 and 59.
- If none of those are true, the final `else` block handles every remaining case, which here means anyone aged 60 or above.
**Only one branch ever runs.** As soon as Python finds a condition that is `True`, it skips all the others.
 
> [!NOTE]
> Order matters. Because Python stops at the first matching condition, the conditions must be arranged so they don't overlap in confusing ways. That is why I tested every age group (see below).
 
### Step 6: Use Formatted Strings (f-strings)
 
One feature I particularly liked is Python's **formatted string**, usually called an **f-string**. Instead of writing:
 
```python
print("Hello " + name)
```
 
I wrote:
 
```python
print(f"Hello {name}")
```
 
The `f` before the quotation marks tells Python to replace anything inside curly braces `{}` with the variable's value. For example:
 
```python
name = "Clinton"
```
 
produces:
 
```text
Hello Clinton
```
 
F-strings keep code cleaner and easier to read, especially when several variables appear in one sentence.
 
### Step 7: Save and Run the Program
 
I saved the file with:
 
```text
Ctrl + S
```
 
Then I opened the integrated terminal in VS Code:
 
```text
Terminal → New Terminal
```
 
and ran the script with:
 
```text
python movie_recommendation.py
```
 
Python immediately ran the program and started asking my questions. Seeing my own code talk back to me for the first time was satisfying, because it confirmed that every part of the program was working together.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/a12a388d-28c4-43ef-8d3e-9bae39fd21aa" />
The VS Code integrated terminal at the `python-practice` folder after running `python movie_recommendation.py`, with the first prompt `What is your name?` visible.
 
### Complete Script
 
For reference, this is the complete program assembled from the steps above:
 
```python
# Greet the user
print("Welcome to the Movie Recommender!")
 
# Ask for the user's name
name = input("What is your name? ")
 
# Ask for the user's age and convert it to an integer
age = int(input("How old are you? "))
 
# Recommend a movie category based on age
if age < 10:
    print(f"Hi {name}! We recommend animated movies like Toy Story or Moana.")
 
elif age >= 10 and age < 18:
    print(f"Hey {name}, you might enjoy teen adventure movies like Harry Potter or Spider-Man.")
 
elif age >= 18 and age < 60:
    print(f"{name}, you might enjoy dramas, thrillers, or action movies.")
 
else:
    print(f"{name}, you may enjoy classics or light comedies.")
```
 
### Step 8: Test Different Inputs
 
Testing is one of the most important habits I have picked up. Instead of assuming my code worked, I deliberately tested one age from every branch of the decision logic.
 
#### Test 1: Dan, age 41
 
```text
Welcome to the Movie Recommender!
 
What is your name? Dan
 
How old are you? 41
 
Dan, you might enjoy dramas, thrillers, or action movies.
```
 
Since 41 falls between 18 and 59, Python correctly selected the third condition.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/6c083892-6aca-4f46-b19a-191963e350bf" />
 The terminal output of the run with name `Dan` and age `41`, ending with the "dramas, thrillers, or action movies" recommendation.
 
#### Test 2: Anakin, age 12
 
```text
Welcome to the Movie Recommender!
 
What is your name? Anakin
 
How old are you? 12
 
Hey Anakin, you might enjoy teen adventure movies like Harry Potter or Spider-Man.
```
 
Age 12 satisfied the second condition, which confirmed my `elif` was working.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/9b8fb6cc-2ae4-42ad-b00a-06d2703e4382" />
 The terminal output of the run with name `Anakin` and age `12`, ending with the teen adventure recommendation.
 
#### Test 3: Bobby, age 9
 
```text
Welcome to the Movie Recommender!
 
What is your name? Bobby
 
How old are you? 9
 
Hi Bobby! We recommend animated movies like Toy Story or Moana.
```
 
Since 9 is less than 10, the first `if` statement ran exactly as expected.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/72afba2d-0571-48d5-9ba4-615ff0e4d5bd" />
The terminal output of the run with name `Bobby` and age `9`, ending with the animated movies recommendation.
 
#### Test 4: Margaret, age 67
 
```text
Welcome to the Movie Recommender!
 
What is your name? Margaret
 
How old are you? 67
 
Margaret, you may enjoy classics or light comedies.
```
 
This confirmed that the `else` block handled ages of 60 and above.
 
  <img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/9eb6d5ef-71c6-40cd-ad0b-ab838976ca38" />
The terminal output of the run with name `Margaret` and age `67`, ending with the classics or light comedies recommendation.
  
### ✅ Verification & Testing: Project 1
 
**Purpose:** Prove that every branch of the `if` / `elif` / `else` logic runs when it should.
 
| Test | Input (Name, Age) | Branch Expected | Expected Result | Actual Result | Status |
| ---- | ----------------- | --------------- | --------------- | ------------- | ------ |
| 1 | Dan, 41 | Third condition (18 to 59) | Dramas, thrillers, or action movies | Dramas, thrillers, or action movies | ✅ |
| 2 | Anakin, 12 | `elif` (10 to 17) | Teen adventure movies | Teen adventure movies | ✅ |
| 3 | Bobby, 9 | `if` (under 10) | Animated movies | Animated movies | ✅ |
| 4 | Margaret, 67 | `else` (60 and above) | Classics or light comedies | Classics or light comedies | ✅ |
 
**Outcome:** All four age groups produced the right recommendation. I now trust that my program behaves exactly as I intended.
 
### Why This Matters
 
- **What it accomplishes:** The program no longer follows one fixed list of instructions. It chooses what to do based on information the user provides.
- **Why it matters in production:** The same pattern (collect input, store it, decide, respond) is the foundation of registration systems, online forms, customer portals, and recommendation engines.
- **What could go wrong:** If I skipped `int()`, the age comparisons would fail with an error. If my conditions were written in the wrong order, some users would get the wrong recommendation.
### What I Learned
 
By completing this project, I learned how to:
 
- Display information using `print()`.
- Collect keyboard input using `input()`.
- Store information in variables.
- Convert text input into integers using `int()`.
- Use comparison operators to evaluate conditions.
- Build decision-making logic with `if`, `elif`, and `else`.
- Personalise output with formatted strings (f-strings).
- Test different inputs to verify that every part of the program works.
### Optional Challenge I Set Myself
 
Once the recommender worked, I wanted to push it further. Instead of using age alone, I considered asking an extra question, like whether the user enjoys comedy, action, or science fiction, and combining the answer with their age for a more personal recommendation. For example:
 
```python
genre = input("Do you enjoy comedy movies? (yes/no): ")
 
if genre.lower() == "yes":
    print("You might enjoy comedy classics!")
 
else:
    print("You might enjoy action or adventure films!")
```
 
This helped me realise that even complex recommendation systems start with the same building blocks I used here. Platforms like Netflix or Disney+ use far more data and much more sophisticated algorithms, but at their core they still collect information, evaluate conditions, and make decisions based on user input.
 
<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/850416dc-3d0d-4245-9f7b-d6bc317c7be7" />
The optional genre challenge code in VS Code and its output when answering `yes` or `no`.
 
---
