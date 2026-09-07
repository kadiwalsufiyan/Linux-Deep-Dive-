# 🔐 𝕃𝕒𝕓 𝟞: ℙ𝕖𝕣𝕞𝕚𝕤𝕤𝕚𝕠𝕟𝕤 𝕒𝕟𝕕 𝕌𝕤𝕖𝕣 𝕄𝕒𝕟𝕒𝕘𝕖𝕞𝕖𝕟𝕥

***

## 🎯 O̶b̶j̶e̶c̶t̶i̶v̶e̶s̶

By the end of this lab, you will be able to:

* 𝙐𝙣𝙙𝙚𝙧𝙨𝙩𝙖𝙣𝙙 𝙖𝙣𝙙 𝙢𝙤𝙙𝙞𝙛𝙮 file permissions using chmod, chown, and chgrp.
* 𝘼𝙪𝙩𝙤𝙢𝙖𝙩𝙚 𝙪𝙨𝙚𝙧 𝙘𝙧𝙚𝙖𝙩𝙞𝙤𝙣 and permission assignment using shell scripting.
* 𝙈𝙖𝙣𝙖𝙜𝙚 𝙪𝙨𝙚𝙧𝙨 𝙖𝙣𝙙 𝙜𝙧𝙤𝙪𝙥𝙨 using useradd, usermod, and related commands.

***

## 📌 P̵r̵e̵r̵e̵r̵e̵r̵e̵q̵u̵i̵s̵i̵t̵e̵s̵

* 💻 A Linux-based system (Ubuntu 22.04 LTS recommended).
* ⚙️ Terminal access with sudo privileges.
* 🔑 Basic familiarity with Linux command line.

***

## 🛠️ L̶a̶b̶ ̶T̶a̶s̶k̶s̶

### 🛠️ Task 1: File Permission Management

#### 🔍 Subtask 1.1: Understanding File Permissions

1. Open a terminal and create a test file:

$ touch testfile.txt

2. View current permissions:

$ ls -l testfile.txt

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: -rw-r--r-- 1 user user 0 Jan 1 10:00 testfile.txt  
> 💡 𝑁𝑜𝑡𝑒: Shows read/write for owner, read-only for group/others.

---

#### 🔎 Subtask 1.2: Modify Permissions with chmod

1. Grant execute permission to the owner:

$ chmod u+x testfile.txt

2. Verify changes:

$ ls -l testfile.txt

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: -rwxr--r-- 1 user user 0 Jan 1 10:00 testfile.txt

3. Revoke read permission for others:

$ chmod o-r testfile.txt

> ⚠️ 𝑇𝑟𝑜𝑢𝑏𝑙𝑒𝑠ℎ𝑜𝑜𝑡𝑖𝑛𝑔: Use sudo if you encounter "Permission denied."

---

#### 🏷️ Subtask 1.3: Change Ownership with chown and chgrp

1. Change the file owner to root (requires sudo):

$ sudo chown root testfile.txt

2. Change the group ownership:

$ sudo chgrp sudo testfile.txt

3. Verify changes:

$ ls -l testfile.txt

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: -rwxr--r-- 1 root sudo 0 Jan 1 10:00 testfile.txt

***

### ⚙️ Task 2: Automate User Creation and Permissions

#### 📜 Subtask 2.1: Write a User Creation Script

1. Create a script create_users.sh:

$ nano create_users.sh

2. Add the following code:

#!/bin/bash  
# Script to create users and assign permissions  
sudo useradd -m -s /bin/bash user1  
sudo passwd user1  # Set password when prompted  
sudo mkdir /home/user1/data  
sudo chown user1:user1 /home/user1/data  
sudo chmod 750 /home/user1/data

3. Make the script executable:

$ chmod +x create_users.sh

4. Run the script:

$ ./create_users.sh

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: User user1 is created with a home directory.  
> 📌 𝑁𝑜𝑡𝑒: /home/user1/data has permissions drwxr-x---.

***

### 👥 Task 3: User Management with useradd

#### 👤 Subtask 3.1: Create and Modify Users

1. Create a new user:

$ sudo useradd -m -s /bin/bash labuser

2. Set a password:

$ sudo passwd labuser

3. Add the user to the sudo group:

$ sudo usermod -aG sudo labuser

4. Verify group membership:

$ groups labuser

> 💬 𝐄𝐱𝐩𝐞𝐜𝐭𝐞𝐝 𝐎𝐮𝐭𝐜𝐨𝐦𝐞: labuser : labuser sudo

---

#### ❌ Subtask 3.2: Delete a User

1. Delete the user and their home directory:

$ sudo userdel -r labuser

> 💡 𝑁𝑜𝑡𝑒: Omit -r to preserve the home directory.

***

## 🏁 C̶o̶n̶c̶l̶u̶s̶i̶o̶n̶

In this lab, you:

* 𝙋𝙧𝙖𝙘𝙩𝙞𝙘𝙚𝙙 𝙢𝙤𝙙𝙞𝙛𝙮𝙞𝙣𝙜 file permissions using chmod, chown, and chgrp.
* 𝘼𝙪𝙩𝙤𝙢𝙖𝙩𝙚𝙙 𝙪𝙨𝙚𝙧 𝙘𝙧𝙚𝙖𝙩𝙞𝙤𝙣 and permission assignment via scripting.
* 𝙈𝙖𝙣𝙖𝙜𝙚𝙙 𝙪𝙨𝙚𝙧𝙨 and groups using useradd and usermod.

💡 𝙆𝙚𝙮 𝙏𝙖𝙠𝙚𝙖𝙬𝙖𝙮𝙨:
* Permissions are critical for system security.
* Automation reduces repetitive administrative tasks.
* Always verify changes with commands like ls -l or groups.

🚀 𝐍𝐞𝐱𝐭 𝐒𝐭𝐞𝐩𝐬:
* Explore ACLs (Access Control Lists) for advanced permissions.
* Learn about sudoers file for granular privilege management.