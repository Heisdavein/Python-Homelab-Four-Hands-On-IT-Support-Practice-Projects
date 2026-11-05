# Python-Homelab-Four-Hands-On-IT-Support-Practice-Projects

Author: Clinton Kehinde Focus: Python fundamentals for IT Support, Help Desk, and Systems Administration roles Environment: Windows 11 · Python 3 · Visual Studio Code

<img width="1672" height="941" alt="image" src="https://github.com/user-attachments/assets/b28e86be-7265-4f0b-83bb-c02ca2530386" />

📑 Table of Contents

Project Overview
Objectives
Technologies Used
Lab Environment
Project Structure
Setting Up My Environment
Project 1: Age-Based Movie Recommender
Project 2: Password Strength Checker
Project 3: IT Support Employee Login Validator
Project 4: Python Error Detective
Challenges Encountered and Solutions Implemented
Security Considerations
Production Considerations
Best Practices I Followed
Lessons Learned
Future Improvements
Conclusion


📌 Project Overview

Python is used almost everywhere in IT. People working in IT Support, Systems Administration, Cybersecurity, Cloud Computing, and Network Engineering use it to automate boring repetitive jobs, process data, troubleshoot systems, and build small tools that save time. As I kept building my technical skills, I realised I wanted more than theory. I wanted hands-on experience writing real programs that solve simple problems.

This repository documents four beginner-friendly Python projects that I built while preparing for IT Support and Help Desk roles. Each project is small, but together they cover the fundamentals that show up again and again in everyday scripting and automation:

Collecting user input
Making decisions with conditional statements
Repeating tasks with loops
Validating what users type
Understanding Python's error messages instead of being scared of them

I didn't want this to be a pile of random code samples. I wanted it to work as a complete guide that someone else could follow from start to finish. For every project I explain not only what I typed, but also why I typed it, what I expected to happen, and how I checked that it worked.

[!NOTE] This guide is written in the first person on purpose. It is both technical documentation and a personal record of what I learned. Screenshot placeholders mark the points where I paused to verify that something worked.

The Four Projects at a Glance
#	Project	Main Concepts Practised	File
1	Age-Based Movie Recommender	print(), input(), variables, int(), f-strings, comparison operators, if / elif / else	movie_recommendation.py
2	Password Strength Checker	while loops, for loops, Boolean variables, string methods, continue, break, input validation	password_checker.py
3	IT Support Employee Login Validator	while True, try / except, ValueError, break, input validation	login_validator.py
4	Python Error Detective	Reading tracebacks, debugging, SyntaxError, NameError, TypeError, ValueError, ZeroDivisionError	error_task1.py to error_task6.py and a bonus calculator
🎯 Objectives
Set up a clean Python development environment on Windows 11.
Write interactive programs that collect and process user input.
Build programs that make decisions using if, elif, and else.
Use while and for loops to repeat tasks without duplicating code.
Validate user input so programs don't crash when someone types the wrong thing.
Handle errors gracefully with try and except.
Learn to read Python error messages (tracebacks) and fix problems one step at a time.
Document my work like a professional so that others (and future me) can rebuild every program from scratch.
🧰 Technologies Used
Technology	What It Is	Why I Used It
Python 3	A popular, beginner-friendly programming language	It is widely used in IT for automation and troubleshooting
Visual Studio Code (VS Code)	A free code editor from Microsoft	Syntax highlighting, IntelliSense, and an integrated terminal in one place
Python extension for VS Code	Microsoft's official extension	Adds code completion, syntax checking, debugging, and one-click running
Windows Command Prompt / VS Code terminal	A text-based way to run commands	Used to verify the install and run my scripts
python.org	The official Python website	A safe, trusted place to download Python
🖥️ Lab Environment

All four projects were completed on my personal Windows 11 computer. I deliberately used the hardware I already owned to show that learning Python does not need an expensive workstation.

Component	Specification
Processor	Intel Core i5 (4 cores)
Memory (RAM)	8 GB
Storage	256 GB SSD
Operating System	Windows 11
Why These Specifications Are More Than Enough

Beginner Python puts very little demand on a computer, unlike machine learning, game development, or video editing.

The Intel Core i5 runs simple Python scripts almost instantly.
8 GB of RAM comfortably runs Windows 11 and a code editor at the same time without noticeable slowdowns.
Every project is text-based, so there is almost no graphics load and only a tiny amount of storage is used.

[!NOTE] None of the four projects needs high-end hardware. Python is a lightweight interpreted language (it reads and runs your code line by line), and these are simple console programs. Even computers with lower specifications should have no trouble following this guide.

📸 Screenshot Placeholder Insert screenshot showing: The Windows 11 Settings → System → About page displaying the processor (Intel Core i5), installed RAM (8 GB), and Windows 11 edition.

📁 Project Structure

Every script lives in a single folder called python-practice on my desktop. I explain why in Step 6 of the setup.

text
python-practice/
├── movie_recommendation.py     # Project 1: Age-Based Movie Recommender
├── password_checker.py         # Project 2: Password Strength Checker
├── login_validator.py          # Project 3: IT Support Employee Login Validator
├── error_task1.py              # Project 4, Task 1: SyntaxError
├── error_task2.py              # Project 4, Task 2: NameError
├── error_task3.py              # Project 4, Task 3: TypeError
├── error_task4.py              # Project 4, Task 4: ValueError
├── error_task5.py              # Project 4, Task 5: ZeroDivisionError
├── error_task6.py              # Project 4, Task 6: Multiple errors in one program
└── (bonus)                     # Project 4, Step 8: Crash-proof calculator

