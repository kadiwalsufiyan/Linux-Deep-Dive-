# 📜 𝕃𝕒𝕓 𝟝: 𝕄𝕒𝕟𝕒𝕘𝕚𝕟𝕘 𝕃𝕠𝕘 𝔽𝕚𝕝𝕖𝕤 𝕚𝕟 𝕃𝕚𝕟𝕦𝕩

***

## 🎯 O̶b̶j̶e̶c̶t̶i̶v̶e̶s̶

By the end of this lab, you will be able to:

* 𝙑𝙞𝙚𝙬 𝙖𝙣𝙙 𝙛𝙞𝙡𝙩𝙚𝙧 log files using commands like cat, less, tail, and grep.
* 𝘼𝙪𝙩𝙤𝙢𝙖𝙩𝙚 𝙡𝙤𝙜 𝙖𝙣𝙖𝙡𝙮𝙨𝙞𝙨 by writing a Bash script to scan for errors.
* 𝘾𝙤𝙣𝙛𝙞𝙜𝙪𝙧𝙚 𝙡𝙤𝙜 𝙧𝙤𝙩𝙖𝙩𝙞𝙤𝙣 using logrotate to manage log file size and retention.

***

## 📌 P̵r̵e̵r̵e̵q̵u̵i̵s̵i̵t̵e̵s̵

* 💻 A Linux-based system (Ubuntu 20.04+ or CentOS 7+ recommended).
* ⚙️ Basic familiarity with the Linux command line.
* 🔑 Sudo or root access for log rotation configuration.

***

## 🛠️ L̶a̶b̶ ̶T̶a̶s̶k̶s̶

### 🛠️ Task 1: Viewing and Filtering Log Files

#### 🔍 Subtask 1.1: View Logs with cat, less, and tail

1. 𝙐𝙨𝙞𝙣𝙜 𝙘𝙖𝙩

Open a terminal and run:

$ cat /var/log/syslog

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: The entire content of /var/log/syslog is displayed.  
> 💡 𝑇𝑖𝑝: Use cat for small log files. For large files, prefer less or tail.

2. 𝙐𝙨𝙞𝙣𝙜 𝙡𝙚𝙨𝙨

Run:

$ less /var/log/syslog

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: The log opens in a scrollable interface. Press q to exit.  
> 💡 𝑇𝑖𝑝: Use / to search for keywords (e.g., /error).

3. 𝙐𝙨𝙞𝙣𝙜 𝙩𝙖𝙞𝙡

To view the last 10 lines:

$ tail /var/log/syslog

To follow new log entries in real-time:

$ tail -f /var/log/syslog

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: New log entries appear as they are written.

---

#### 🔎 Subtask 1.2: Filter Logs with grep

1. Search for "error" in /var/log/syslog:

$ grep -i "error" /var/log/syslog

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: Lines containing "error" (case-insensitive) are displayed.  
> 💡 𝑇𝑖𝑝: Use -A 2 to show 2 lines after the match (e.g., grep -i -A 2 "error").

***

### ⚙️ Task 2: Automate Log Analysis with a Bash Script

#### 📜 Subtask 2.1: Create a Script to Scan for Errors

1. Create a file named log_analyzer.sh:

$ nano log_analyzer.sh

2. Add the following script:

#!/bin/bash  
LOG_FILE="/var/log/syslog"  
ERROR_KEYWORDS=("error" "failed" "warning")  

echo "Scanning $LOG_FILE for errors..."  
for keyword in "${ERROR_KEYWORDS[@]}"; do  
    echo "=== $keyword ==="  
    grep -i "$keyword" "$LOG_FILE"  
done

3. Save the file and make it executable:

$ chmod +x log_analyzer.sh

4. Run the script:

$ ./log_analyzer.sh

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: The script outputs lines containing "error", "failed", or "warning".  
> ⚠️ 𝑇𝑟𝑜𝑢𝑏𝑙𝑒𝑠ℎ𝑜𝑜𝑡𝑖𝑛𝑔: Ensure the script has execute permissions (chmod +x).

***

### 🔄 Task 3: Configure Log Rotation with logrotate

#### ⚙️ Subtask 3.1: Create a Custom Log Rotation Policy

1. Create a configuration file for a sample log (/var/log/myapp.log):

$ sudo nano /etc/logrotate.d/myapp

2. Add the following rules:

/var/log/myapp.log {  
    daily  
    rotate 7  
    compress  
    missingok  
    notifempty  
    create 0640 root adm  
}

📌 𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧:
* 𝑑𝑎𝑖𝑙𝑦: Rotate logs daily.
* 𝑟𝑜𝑡𝑎𝑡𝑒 7: Keep 7 rotated logs.
* 𝑐𝑜𝑚𝑝𝑟𝑒𝑠𝑠: Compress old logs (e.g., .gz).
* 𝑐𝑟𝑒𝑎𝑡𝑒 0640 𝑟𝑜𝑜𝑡 𝑎𝑑𝑚: Set permissions for new log files.

3. Test the configuration:

$ sudo logrotate -d /etc/logrotate.d/myapp

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: Debug output shows the rotation plan (no changes made).

4. Force a rotation:

$ sudo logrotate -vf /etc/logrotate.d/myapp

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: Logs are rotated if /var/log/myapp.log exists.

***

## 🏁 C̶o̶n̶c̶l̶u̶s̶i̶o̶n̶

In this lab, you learned to:

* 𝙑𝙞𝙚𝙬 𝙖𝙣𝙙 𝙛𝙞𝙡𝙩𝙚𝙧 logs using cat, less, tail, and grep.
* 𝘼𝙪𝙩𝙤𝙢𝙖𝙩𝙚 𝙚𝙧𝙧𝙤𝙧 𝙙𝙚𝙩𝙚𝙘𝙩𝙞𝙤𝙣 with a Bash script.
* 𝘾𝙤𝙣𝙛𝙞𝙜𝙪𝙧𝙚 𝙡𝙤𝙜 𝙧𝙤𝙩𝙖𝙩𝙞𝙤𝙣 to manage log file size and retention.

These skills are critical for Linux system administrators to maintain and troubleshoot systems efficiently.

🚀 𝐍𝐞𝐱𝐭 𝐒𝐭𝐞𝐩𝐬:
* Explore advanced grep options like -B (before) and -C (context).
* Extend the Bash script to email alerts for critical errors.
* Experiment with logrotate options like size (rotate by size) or postrotate scripts.