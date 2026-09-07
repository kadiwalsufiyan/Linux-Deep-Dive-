# Lab 4: Working with Text Files

***

## Objectives

By the end of this lab, you will be able to:

* Use cat, grep, awk, and sed to process text files.
* Write a script to search for patterns in log files and process the output.
* Filter, replace, and format text files using command-line tools.

***

## Prerequisites

* A Linux-based system (Ubuntu/CentOS recommended).
* Basic familiarity with the command line.
* Text editor (e.g., nano, vim, or gedit).

***

## Lab Tasks

### Task 1: Basic Text File Operations with cat, grep, awk, and sed

#### Subtask 1.1: Viewing File Contents with cat

1. Open a terminal.

2. Create a sample text file named sample.txt:

$ echo -e "Line 1\nLine 2\nLine 3\nError: File not found\nWarning: Low disk space" > sample.txt

3. View the file contents using cat:

$ cat sample.txt

Expected Output:
Line 1  
Line 2  
Line 3  
Error: File not found  
Warning: Low disk space

#### Subtask 1.2: Searching Text with grep

1. Search for lines containing "Error" in sample.txt:

$ grep "Error" sample.txt

Expected Output:
Error: File not found

2. Use grep -i for case-insensitive search:

$ grep -i "warning" sample.txt

Expected Output:
Warning: Low disk space

#### Subtask 1.3: Text Processing with awk

1. Print the second column of sample.txt (assuming columns are space-separated):

$ awk '{print $2}' sample.txt

Expected Output:
1  
2  
3  
File  
disk

#### Subtask 1.4: Text Replacement with sed

1. Replace "Error" with "Critical" in sample.txt:

$ sed 's/Error/Critical/' sample.txt

Expected Output:
Line 1  
Line 2  
Line 3  
Critical: File not found  
Warning: Low disk space

***

### Task 2: Script to Search and Process Log Files

#### Subtask 2.1: Create a Sample Log File

1. Generate a log file named system.log:

$ echo -e "2023-10-01 10:00:01 INFO: System booted\n2023-10-01 10:05:23 ERROR: Disk full\n2023-10-01 10:10:45 WARNING: High CPU usage" > system.log

#### Subtask 2.2: Write a Script to Filter Logs

1. Create a script named log_parser.sh:

$ nano log_parser.sh

2. Add the following content:

#!/bin/bash  
# Search for ERROR or WARNING in log file  
echo "Errors and Warnings in system.log:"  
grep -E "ERROR|WARNING" system.log

3. Make the script executable:

$ chmod +x log_parser.sh

4. Run the script:

$ ./log_parser.sh

Expected Output:
Errors and Warnings in system.log:  
2023-10-01 10:05:23 ERROR: Disk full  
2023-10-01 10:10:45 WARNING: High CPU usage

***

### Task 3: Advanced Text Filtering and Formatting

#### Subtask 3.1: Filter Specific Columns with awk

1. Extract the timestamp and message from system.log:

$ awk '{print $1, $2, $3, $4}' system.log

Expected Output:
2023-10-01 10:00:01 INFO:  
2023-10-01 10:05:23 ERROR:  
2023-10-01 10:10:45 WARNING:

#### Subtask 3.2: Replace Text in a File with sed

1. Replace "ERROR" with "CRITICAL" in system.log and save to a new file:

$ sed 's/ERROR/CRITICAL/' system.log > system_updated.log

2. Verify the changes:

$ cat system_updated.log

Expected Output:
2023-10-01 10:00:01 INFO: System booted  
2023-10-01 10:05:23 CRITICAL: Disk full  
2023-10-01 10:10:45 WARNING: High CPU usage

***

## Conclusion

In this lab, you learned how to:

* Use cat, grep, awk, and sed for text processing.
* Write a script to filter and analyze log files.
* Perform advanced text filtering and formatting operations.

Troubleshooting Tips:
* If grep returns no results, ensure the search term matches the case (use -i for case-insensitive search).
* If sed replacements don't work, check for special characters in the text (use \ to escape them).
* Ensure scripts have executable permissions (chmod +x).

Next Steps:
* Practice with larger log files (e.g., /var/log/syslog).
* Explore regular expressions for advanced grep and sed usage.