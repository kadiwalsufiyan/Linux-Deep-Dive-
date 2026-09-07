# ⚡ 𝕃𝕒𝕓 𝟟: 𝕀𝕟𝕥𝕣𝕠𝕕𝕦𝕔𝕥𝕚𝕠𝕟 𝕥𝕠 𝔹𝕒𝕤𝕙 𝕊𝕙𝕖𝕝𝕝 𝕊𝕔𝕣𝕚𝕡𝕥𝕚𝕟𝕘

***

## 🎯 O̶b̶j̶e̶c̶t̶i̶v̶e̶s̶

By the end of this lab, you will be able to:

* 𝙐𝙣𝙙𝙚𝙧𝙨𝙩𝙖𝙣𝙙 𝙩𝙝𝙚 𝙛𝙪𝙣𝙙𝙖𝙢𝙚𝙣𝙩𝙖𝙡𝙨 of Bash scripting, including variables, loops, and conditionals.
* 𝙒𝙧𝙞𝙩𝙚 𝙖𝙣𝙙 𝙚𝙭𝙚𝙘𝙪𝙩𝙚 Bash scripts to automate system configuration tasks.
* 𝘾𝙧𝙚𝙖𝙩𝙚 𝙖 𝙨𝙘𝙧𝙞𝙥𝙩 to automate system updates on a Linux machine.

***

## 📌 P̵r̵e̵r̵e̵r̵e̵r̵e̵q̵u̵i̵s̵i̵t̵e̵s̵

* 💻 A Linux-based system (Ubuntu 20.04/22.04 recommended).
* ⚙️ Basic familiarity with Linux command line.
* 🔑 Sudo privileges for system update tasks.

***

## 🛠️ L̶a̶b̶ ̶T̶a̶s̶k̶s̶

### 🛠️ Task 1: Learn the Basics of Bash Scripting

#### 🔍 Subtask 1.1: Create and Execute a Simple Bash Script

1. Open a terminal and create a new file named hello.sh:

$ nano hello.sh

2. Add the following shebang and echo command:

#!/bin/bash  
echo "Hello, World!"

3. Save the file (Ctrl+O, Enter, Ctrl+X).

4. Make the script executable:

$ chmod +x hello.sh

5. Execute the script:

$ ./hello.sh

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: Hello, World!

---

#### 🔎 Subtask 1.2: Use Variables in Bash

1. Edit hello.sh to include variables:

#!/bin/bash  
greeting="Welcome to Bash Scripting"  
echo $greeting

2. Run the script again.

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: Welcome to Bash Scripting

---

#### 𝔖 Subtask 1.3: Implement a Conditional Statement

1. Modify hello.sh to check a condition:

#!/bin/bash  
if [ "$1" == "admin" ]; then  
  echo "Welcome, Administrator!"  
else  
  echo "Access Denied"  
fi

2. Run the script with an argument:

$ ./hello.sh admin

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: Welcome, Administrator!

---

#### 🔄 Subtask 1.4: Create a Loop

1. Update hello.sh to include a for loop:

#!/bin/bash  
for i in {1..5}; do  
  echo "Iteration $i"  
done

2. Execute the script.

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞:
> Iteration 1  
> Iteration 2  
> Iteration 3  
> Iteration 4  
> Iteration 5

***

### ⚙️ Task 2: Automate System Configuration

#### 🖥️ Subtask 2.1: Write a Script to Set Hostname

1. Create set_hostname.sh:

#!/bin/bash  
NEW_HOSTNAME="lab-machine"  
sudo hostnamectl set-hostname $NEW_HOSTNAME  
echo "Hostname set to $NEW_HOSTNAME"

2. Make it executable and run with sudo:

$ chmod +x set_hostname.sh  
$ sudo ./set_hostname.sh

3. Verify:

$ hostname

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: lab-machine

---

#### 👤 Subtask 2.2: Add Users via Script

1. Create add_user.sh:

#!/bin/bash  
USERNAME="testuser"  
sudo useradd -m $USERNAME  
echo "User $USERNAME created."

2. Execute and verify:

$ id testuser

***

### 🔄 Task 3: Automate System Updates

#### 🚀 Subtask 3.1: Create an Update Script

1. Write system_update.sh:

#!/bin/bash  
echo "Starting system update..."  
sudo apt update && sudo apt upgrade -y  
echo "Updates completed!"

2. Run with sudo:

$ sudo ./system_update.sh

---

#### ⏰ Subtask 3.2: Schedule Updates with Cron

1. Open crontab:

$ crontab -e

2. Add this line to run weekly:

0 3 * * 0 /path/to/system_update.sh >> /var/log/update.log 2>&1

***

## 🏁 C̶o̶n̶c̶l̶u̶s̶i̶o̶n̶

You’ve learned to:

* 𝙒𝙧𝙞𝙩𝙚 𝙗𝙖𝙨𝙞𝙘 Bash scripts with variables, loops, and conditionals.
* 𝘼𝙪𝙩𝙤𝙢𝙖𝙩𝙚 𝙨𝙮𝙨𝙩𝙚𝙢 tasks like hostname configuration and user management.
* 𝙎𝙘𝙝𝙚𝙙𝙪𝙡𝙚 𝙪𝙥𝙙𝙖𝙩𝙚𝙨 using cron.

💡 𝙆𝙚𝙮 𝙏𝙖𝙠𝙚𝙖𝙬𝙖𝙮𝙨: Bash scripting is a powerful tool for Linux administrators to automate repetitive tasks efficiently.

⚠️ 𝐓𝐫𝐨𝐮𝐛𝐥𝐞𝐬𝐡𝐨𝐨𝐭𝐢𝐧𝐠 𝐓𝐢𝐩𝐬:
* 𝑃𝑒𝑟𝑚𝑖𝑠𝑠𝑖𝑜𝑛 𝐷𝑒𝑛𝑖𝑒𝑑: Use chmod +x to make scripts executable.
* 𝑆𝑦𝑛𝑡𝑎𝑥 𝐸𝑟𝑟𝑜𝑟𝑠: Debug with bash -x script.sh.
* 𝐶𝑟𝑜𝑛 𝐼𝑠𝑠𝑢𝑒𝑠: Check logs at /var/log/syslog.

🚀 𝐍𝐞𝐱𝐭 𝐒𝐭𝐞𝐩𝐬: Explore advanced topics like functions, error handling, and interacting with APIs in Bash.