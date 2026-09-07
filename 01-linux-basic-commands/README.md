# Lab 1: Introduction to Linux Basic Commands

***

## Objectives

By the end of this lab, you will be able to:

* Understand and execute basic Linux commands (ls, cd, pwd, mkdir, rm).
* Navigate directories and manage files efficiently.
* Write a simple Bash script to automate file and directory creation.

***

## Prerequisites

* A Linux-based operating system (e.g., Ubuntu, Fedora, or Debian).
* Terminal access (Ctrl+Alt+T or search for "Terminal" in applications).
* Basic familiarity with using a command-line interface (CLI).

***

## Lab Tasks

### Task 1: Learn Basic Linux Commands

#### Subtask 1.1: List Directory Contents (ls)

1. Open the terminal.
2. Type the following command to list files and directories in the current folder:

ls

Expected Outcome: A list of files and directories in your current location.  
Explanation: ls stands for "list" and displays the contents of the current directory.

3. To view detailed information (permissions, size, etc.), use:

ls -l

Explanation: The -l flag provides a long listing format.

4. To show hidden files (those starting with a dot), use:

ls -a

Explanation: The -a flag shows all files, including hidden ones.

***

#### Subtask 1.2: Navigate Directories (cd) and Print Working Directory (pwd)

1. Check your current directory with:

pwd

Expected Outcome: The full path of your current directory (e.g., /home/username).

2. Navigate to your home directory:

cd ~

Explanation: ~ is a shortcut for the home directory.

3. Move into a subdirectory (e.g., Documents):

cd Documents

Troubleshooting: If the directory doesn’t exist, you’ll see an error. Use ls to verify.

4. Return to the previous directory:

cd ..

Explanation: .. refers to the parent directory.

***

#### Subtask 1.3: Create and Remove Directories (mkdir, rm)

1. Create a new directory named test_folder:

mkdir test_folder

Expected Outcome: A new directory named test_folder is created.

2. Verify the creation:

ls

3. Remove the directory (must be empty):

rmdir test_folder

Explanation: rmdir removes empty directories.

4. To remove a directory and its contents recursively:

rm -r test_folder

> Warning: This is irreversible. Use with caution.

***

### Task 2: Practice Navigating and Managing Files

#### Subtask 2.1: Create and Delete Files

1. Create a file named example.txt:

touch example.txt

Explanation: touch creates an empty file.

2. Delete the file:

rm example.txt

***

#### Subtask 2.2: Copy and Move Files

1. Recreate example.txt:

touch example.txt

2. Copy the file to a new name:

cp example.txt example_copy.txt

3. Move the file to a different directory (e.g., Documents):

mv example_copy.txt ~/Documents/

***

### Task 3: Write a Script to Automate File/Directory Creation

#### Subtask 3.1: Create a Bash Script

1. Open a text editor (e.g., nano):

nano create_files.sh

2. Add the following code to the script:

#!/bin/bash  
# This script creates directories and files  
mkdir -p lab_files  
cd lab_files  
touch file1.txt file2.txt file3.txt  
echo "Files created successfully!"

Explanation:
* #!/bin/bash specifies the interpreter.
* mkdir -p creates a directory (ignores errors if it exists).
* touch creates multiple files.

3. Save and exit (Ctrl+O, Enter, Ctrl+X in nano).

4. Make the script executable:

chmod +x create_files.sh

5. Run the script:

./create_files.sh

Expected Outcome: A lab_files directory with three empty files.

***

## Conclusion

In this lab, you:

* Learned essential Linux commands (ls, cd, pwd, mkdir, rm).
* Practiced navigating directories and managing files.
* Created a Bash script to automate file/directory creation.

These skills are foundational for Linux system administrators and will help you manage systems efficiently. Practice regularly to build confidence!

Next Steps: Explore advanced commands (grep, chmod, find) and scripting.