🐧 Lab 1: Introduction to Linux Basic Commands

---

📌 Lab Objectives

By completing this lab, you will learn how to:

- Use basic Linux commands.
- Navigate between directories.
- Create and remove files and directories.
- Copy and move files.
- Create and execute a basic Bash script.

---

🖥️ Prerequisites

Before starting this lab, you need:

- A Linux operating system (Ubuntu, Debian, Fedora, etc.)
- Terminal access
- Basic knowledge of the Linux command line

---

🚀 Task 1: Basic Linux Commands

---

🔹 Command 1: "ls"

📌 Purpose

The "ls" command is used to list files and directories.

💻 Command

ls

📖 Explanation

This command displays the files and directories available in the current location.

🎯 Expected Result

You will see a list of files and directories.

---

🔹 Command 2: "ls -l"

📌 Purpose

Display detailed information about files and directories.

💻 Command

ls -l

📖 Explanation

The "-l" option shows information such as:

- File permissions
- File owner
- File size
- Modification date

---

🔹 Command 3: "ls -a"

📌 Purpose

Display all files, including hidden files.

💻 Command

ls -a

📖 Explanation

Files starting with "." are hidden files in Linux.

---

📂 Task 2: Directory Navigation

---

🔹 Command 4: "pwd"

📌 Purpose

Display the current working directory.

💻 Command

pwd

🎯 Expected Result

You will see the full path of your current directory.

Example:

/home/username

---

🔹 Command 5: "cd ~"

📌 Purpose

Navigate to the user's home directory.

💻 Command

cd ~

📖 Explanation

The "~" symbol represents the current user's home directory.

---

🔹 Command 6: "cd Documents"

📌 Purpose

Move into the "Documents" directory.

💻 Command

cd Documents

⚠️ Note

The directory must exist. Use "ls" to check available directories.

---

🔹 Command 7: "cd .."

📌 Purpose

Move to the parent directory.

💻 Command

cd ..

📖 Explanation

The ".." symbol represents the parent directory.

---

📁 Task 3: Directory Management

---

🔹 Command 8: "mkdir"

📌 Purpose

Create a new directory.

💻 Command

mkdir test_folder

🎯 Expected Result

A directory named "test_folder" will be created.

---

🔹 Command 9: "rmdir"

📌 Purpose

Remove an empty directory.

💻 Command

rmdir test_folder

⚠️ Important

This command works only if the directory is empty.

---

🔹 Command 10: "rm -r"

📌 Purpose

Remove a directory and its contents.

💻 Command

rm -r test_folder

⚠️ Warning

This command permanently deletes files and directories. Use it carefully.

---

📄 Task 4: File Management

---

🔹 Command 11: "touch"

📌 Purpose

Create an empty file.

💻 Command

touch example.txt

🎯 Expected Result

A new empty file named "example.txt" will be created.

---

🔹 Command 12: "rm"

📌 Purpose

Delete a file.

💻 Command

rm example.txt

⚠️ Warning

Deleted files may not be easily recoverable.

---

🔹 Command 13: "cp"

📌 Purpose

Copy a file.

💻 Command

cp example.txt example_copy.txt

📖 Explanation

This creates a copy of "example.txt" named "example_copy.txt".

---

🔹 Command 14: "mv"

📌 Purpose

Move or rename files.

💻 Command

mv example_copy.txt ~/Documents/

🎯 Expected Result

The file will be moved to the "Documents" directory.

---

⚙️ Task 5: Bash Scripting

---

🔹 Step 1: Create the Script

💻 Command

nano create_files.sh

This creates and opens a new Bash script.

---

🔹 Step 2: Add the Script Code

💻 Bash Script

#!/bin/bash

# This script creates directories and files

mkdir -p lab_files

cd lab_files || exit

touch file1.txt file2.txt file3.txt

echo "Files created successfully!"

📖 Script Explanation

Command| Purpose
"#!/bin/bash"| Specifies the Bash interpreter
"mkdir -p lab_files"| Creates the directory
"cd lab_files"| Moves into the directory
"touch"| Creates empty files
"echo"| Displays a message

---

🔹 Step 3: Make the Script Executable

💻 Command

chmod +x create_files.sh

📖 Explanation

This gives execute permission to the script.

---

🔹 Step 4: Run the Script

💻 Command

./create_files.sh

🎯 Expected Result

The following structure will be created:

lab_files/
├── file1.txt
├── file2.txt
└── file3.txt

---

🧠 Skills Practiced

- Linux Command Line
- Directory Navigation
- File Management
- Basic Linux Commands
- Bash Scripting
- File Permissions

---

✅ Conclusion

In this lab, I practiced essential Linux commands used for navigating directories and managing files.

I also created and executed a Bash script to automate file and directory creation.

These are fundamental skills required for a Linux System Administrator.