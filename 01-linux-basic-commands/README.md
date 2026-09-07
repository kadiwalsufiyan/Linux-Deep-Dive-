Lab 1: Introduction to Linux Basic Commands

Objectives

By the end of this lab, you will be able to:

- Understand and execute basic Linux commands such as "ls", "cd", "pwd", "mkdir", and "rm".
- Navigate directories and manage files efficiently.
- Write a simple Bash script to automate file and directory creation.

---

Prerequisites

- A Linux-based operating system such as Ubuntu, Fedora, or Debian.
- Terminal access.
- Basic familiarity with using a command-line interface (CLI).

---

Lab Tasks

Task 1: Learn Basic Linux Commands

Subtask 1.1: List Directory Contents ("ls")

Open the terminal and run:

ls

Expected Outcome: Displays files and directories in the current location.

Explanation: The "ls" command lists the contents of a directory.

For detailed information, use:

ls -l

The "-l" option displays detailed information such as permissions, ownership, and file size.

To display hidden files:

ls -a

The "-a" option shows all files, including hidden files.

---

Subtask 1.2: Navigate Directories ("cd" and "pwd")

Check your current working directory:

pwd

Navigate to your home directory:

cd ~

Move into a subdirectory:

cd Documents

Return to the parent directory:

cd ..

---

Subtask 1.3: Create and Remove Directories

Create a directory:

mkdir test_folder

Verify that it was created:

ls

Remove an empty directory:

rmdir test_folder

Remove a directory and its contents recursively:

rm -r test_folder

«⚠️ Warning: The "rm -r" command can permanently delete files and directories. Use it carefully.»

---

Task 2: Practice File Management

Subtask 2.1: Create and Delete Files

Create an empty file:

touch example.txt

Delete the file:

rm example.txt

---

Subtask 2.2: Copy and Move Files

Create the file again:

touch example.txt

Copy the file:

cp example.txt example_copy.txt

Move the copied file to the Documents directory:

mv example_copy.txt ~/Documents/

---

Task 3: Bash Script for File and Directory Creation

Create the Bash Script

Create a new script:

nano create_files.sh

Add the following script:

#!/bin/bash

# This script creates directories and files

mkdir -p lab_files

cd lab_files || exit

touch file1.txt file2.txt file3.txt

echo "Files created successfully!"

Save and exit the editor.

Make the script executable:

chmod +x create_files.sh

Run the script:

./create_files.sh

Expected Outcome

The script creates:

lab_files/
├── file1.txt
├── file2.txt
└── file3.txt

---

Commands Covered

Command| Purpose
"ls"| List directory contents
"pwd"| Display current directory
"cd"| Change directory
"mkdir"| Create directories
"rmdir"| Remove empty directories
"rm"| Remove files and directories
"touch"| Create empty files
"cp"| Copy files
"mv"| Move or rename files
"chmod"| Change file permissions

---

Skills Demonstrated

- Linux Command Line
- File Management
- Directory Navigation
- Basic Bash Scripting
- Linux System Administration Fundamentals

---

Conclusion

In this lab, I practiced essential Linux commands for navigating directories and managing files.

I also created a Bash script to automate the creation of directories and files.

These commands and scripting skills form an important foundation for Linux System Administration.