# Adding-menu-items
This Menu Management System is a CLI tool for tracking food macros. It uses role-based access: Customers view the menu, while Workers (admin/1234) can add or delete items. Data is saved to menu.txt for persistence. It runs on a continuous loop, handling real-time updates to both memory and local storage until the exit command is used.

Project Overview
This is a Python-based Menu Management System designed to handle food items and their nutritional macros through a command-line interface (CLI). The application utilizes a role-based access system to separate administrative tasks from customer viewing, using a local text file (menu.txt) for persistent data storage.

Usage Flow
To use the system, the user selects a role upon execution. Customers are granted read-only access to view the menu and its nutritional details. Workers must authenticate using a predefined username and password to access administrative tools. Once logged in, a worker can add new dishes—inputting the name, calories, protein, fats, and carbs—which are then appended to the data file. The system also supports an item deletion feature, which removes specific entries from the menu and updates the storage file in real-time. The program runs in a continuous loop, allowing for multiple role switches and operations until the "exit" command is issued.

Honest Mentor Critique: GitHub Readiness
If you are putting this on GitHub to showcase your work, you need to address several "blind spots" that experienced developers will notice immediately.

The Data Integrity Flaw: As currently written, the delete function will likely crash your program if you try to remove an item that was saved in a previous session. This happens because add_items saves data as a list, but load_menu reads it back as a string. To fix this for GitHub, you should ensure data types are consistent (ideally by using a CSV or JSON library).

Security Risk: Hardcoding admin and 1234 is a "bad practice" red flag. For a GitHub portfolio, you should at least add a comment noting that this is for demonstration purposes, or move the credentials to a .env file.

Input Validation: The code assumes the user will always provide the correct data type (e.g., an integer for the number of items). If a user enters a letter instead of a number, the program crashes. Adding basic try/except blocks would significantly improve the "professional" feel of the repository.

File Handling: Replace the manual f.open() and f.close() calls with with open(...) context managers. This is the Pythonic standard and prevents memory leaks or file corruption if the program is interrupted.
