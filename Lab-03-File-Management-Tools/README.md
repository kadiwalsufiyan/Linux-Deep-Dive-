# Lab 3: Working with File Management Tools

***

## Objectives

By the end of this lab, you will be able to:

* Use cp, mv, and rm commands for basic file manipulation.
* Search for files efficiently using the find command.
* Automate file backups using the tar command in a shell script.

***

## Prerequisites

* A Linux-based system (Ubuntu 22.04 LTS or similar).
* Basic familiarity with the terminal.
* Permissions to create, modify, and delete files in your home directory.

***

## Lab Tasks

### Task 1: File Manipulation with cp, mv, and rm

#### Subtask 1.1: Copying Files with cp

1. Open a terminal.

2. Create a test file:

$ echo "This is a test file." > testfile.txt

3. Copy the file to a new location:

$ cp testfile.txt testfile_copy.txt

4. Verify the copy:

$ ls

Expected Outcome: Both testfile.txt and testfile_copy.txt should appear in the directory.

#### Subtask 1.2: Moving/Renaming Files with mv

1. Rename testfile_copy.txt to renamed_file.txt:

$ mv testfile_copy.txt renamed_file.txt

2. Move renamed_file.txt to a new directory:

$ mkdir backup_folder  
$ mv renamed_file.txt backup_folder/

3. Verify the move:

$ ls backup_folder/

Expected Outcome: renamed_file.txt should now be inside backup_folder.

#### Subtask 1.3: Deleting Files with rm

1. Delete testfile.txt:

$ rm testfile.txt

2. Delete the backup_folder and its contents:

$ rm -r backup_folder

Expected Outcome: Both the file and folder should no longer appear in ls.

Troubleshooting Tip: Use $ rm -i for interactive deletion to avoid accidental file loss.

***

### Task 2: Searching for Files with find

#### Subtask 2.1: Basic File Search

1. Create sample files:

$ touch file1.txt file2.log file3.txt

2. Search for all .txt files in the current directory:

$ find . -name "*.txt"

Expected Outcome: Output lists file1.txt and file3.txt.

#### Subtask 2.2: Advanced Search by Size

1. Create a large file (10MB) for testing:

$ dd if=/dev/zero of=largefile bs=1M count=10

2. Find files larger than 5MB:

$ find . -size +5M

Expected Outcome: Output lists largefile.

Troubleshooting Tip: Use $ find . -type f -size +5M to limit results to files only (exclude directories).

***

### Task 3: Automating Backups with tar

#### Subtask 3.1: Create a Backup Script

1. Open a text editor and create backup_script.sh:

#!/bin/bash  
# Backup script for Lab 3  
BACKUP_DIR="./backups"  
SOURCE_DIR="./"  
mkdir -p $BACKUP_DIR  
tar -czvf "$BACKUP_DIR/backup_$(date +%Y%m%d).tar.gz" $SOURCE_DIR/*.txt $SOURCE_DIR/*.log  
echo "Backup completed. Files saved in $BACKUP_DIR."

2. Make the script executable:

$ chmod +x backup_script.sh

3. Run the script:

$ ./backup_script.sh

Expected Outcome: A compressed .tar.gz file is created in the backups directory.

#### Subtask 3.2: Verify the Backup

1. List the backup file:

$ ls backups/

2. Extract the backup to verify:

$ tar -xzvf backups/backup_*.tar.gz -C /tmp/  
$ ls /tmp/

Expected Outcome: Extracted files match the original .txt and .log files.

Troubleshooting Tip: Use -v (verbose) flag in tar to monitor the backup process.

***

## Conclusion

In this lab, you:

* Manipulated files using cp, mv, and rm.
* Searched for files efficiently with find.
* Automated backups using a tar script.

Next Steps:
* Explore rsync for incremental backups.
* Learn about file permissions (chmod, chown) for secure management.

Lab Cleanup:
Delete all test files and directories:

$ rm -rf file*.txt file*.log largefile backups/