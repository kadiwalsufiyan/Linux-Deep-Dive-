# Lab 2: Understanding Linux File Systems

***

## Objectives

By the end of this lab, you will be able to:

* Identify and compare different Linux file system types (ext4, XFS, Btrfs).
* Use command-line tools (df, mount, lsblk) to inspect file systems.
* Create a Bash script to monitor and display file system usage.

***

## Prerequisites

* A Linux-based system (Ubuntu 20.04/22.04 LTS recommended).
* Basic familiarity with Linux terminal commands.
* Sudo or root access (for certain commands).

***

## Lab Tasks

### Task 1: Research Linux File System Types

#### Subtask 1.1: Overview of Common File Systems

Linux supports multiple file systems. The most common are:

* ext4: Default for many distributions, offers journaling and backward compatibility.
* XFS: High-performance for large files, used in enterprise environments.
* Btrfs: Modern file system with features like snapshots and checksums.

#### Subtask 1.2: Check Current File System

Run this command to identify your system's file system(s):

$ lsblk -f

Expected Output:
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT  
sda                                                    
├─sda1 ext4         a1b2c3d4-5678-90ef-ghij-klmnopqr1234 /  
└─sda2 swap         9876zyxw-vuts-rqpo-nmlk-jihgfedcba12 [SWAP]

Key Concept: FSTYPE column shows the file system format for each partition.

***

### Task 2: Inspect File Systems Using CLI Tools

#### Subtask 2.1: Check Disk Space Usage

$ df -hT

Flags Explanation:
* -h: Human-readable format (KB, MB, GB)
* -T: Display file system type

Expected Output:
Filesystem     Type      Size  Used Avail Use% Mounted on  
/dev/sda1      ext4       50G   15G   33G  32% /

#### Subtask 2.2: View Mounted File Systems

$ mount | grep "^/dev"

Expected Output:
/dev/sda1 on / type ext4 (rw,relatime)

#### Subtask 2.3: List Block Devices

$ lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT

Troubleshooting Tip: If outputs are truncated, use $ lsblk -o +FSTYPE for wider format.

***

### Task 3: Create File System Monitoring Script

#### Subtask 3.1: Script Creation

Create fs_monitor.sh:

#!/bin/bash  
  
# Header  
echo "File System Monitoring Report"  
echo "-----------------------------"  
date  
echo  
  
# Disk usage summary  
echo "1. Overall Disk Usage:"  
df -h --output=source,fstype,size,pcent,target | grep -v "tmpfs\|loop"  
  
# Large partitions alert  
echo -e "\n2. Partitions Over 80% Full:"  
df -h | awk 'NR>1 && int($5) > 80 {print $1 " is " $5 " full"}'  
  
# Inode usage  
echo -e "\n3. Inode Usage:"  
df -i | awk 'NR==1 || $5 > 0 {print}'

#### Subtask 3.2: Make Script Executable

$ chmod +x fs_monitor.sh

#### Subtask 3.3: Run the Script

$ ./fs_monitor.sh

Expected Output:
File System Monitoring Report
Wed Jan 10 14:30:00 UTC 2024

1. Overall Disk Usage: 
/dev/sda1 ext4 50G 32% / 
/dev/sdb1 xfs 100G 45% /data

2. Partitions Over 80% Full: 
/dev/sdc1 is 85% full

3. Inode Usage: 
Filesystem Inodes IUsed IFree IUse% Mounted on 
/dev/sda1 1.2M 45K 1.1M 4% /

***

## Conclusion

In this lab, you:

1. Explored key Linux file systems and their characteristics.
2. Practiced essential commands for file system inspection.
3. Developed an automated monitoring script for system administration tasks.

Next Steps:
* Experiment with mkfs to create different file system types.
* Explore advanced Btrfs features like subvolumes.
* Schedule your monitoring script with cron for regular checks.

Final Check: Verify all commands worked as expected and your script outputs match the expected format.