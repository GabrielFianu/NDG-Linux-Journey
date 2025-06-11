# System and User Security. 

## Introduction
In this exercise you  will be able to monitor who has been attempting to log in to the system, and view user and group permissions.

---

## Objectives
Learn the difference between the superuser account and regular user accounts.
View user account information.

---

### 1. Running Commands as an Administrator
In this task, you will learn two ways to run commands as an administrative user. This is often necessary for making changes that affect the whole system.

su -

![Image](https://github.com/user-attachments/assets/406498ab-3de0-4339-a792-59fc5d8089df)

Confirm the new user identity using the id command:

id

![Image](https://github.com/user-attachments/assets/85e40b21-3210-4c94-99e7-e81d7b0210a3)

After using the shell started by the su command to perform the necessary administrative tasks, return to your original shell (and original user account) by using the exit command. 
Confirm the user identity change using the id command.

exit

id

![Image](https://github.com/user-attachments/assets/137c8f5d-c1bd-4d51-b565-f9c13c9afbe7)

![Image](https://github.com/user-attachments/assets/91db5fd4-6348-4184-8e1b-62ef50c1bb7f)

**Exiting the shell is important to avoid executing commands as root that could damage the system.**

The sudo command works on systems that do not allow root access by default. It is preferred for most administrative tasks since root access times out automatically without having to exit. 

First type a command as the sysadmin non-privileged user.

head /etc/shadow               

![Image](https://github.com/user-attachments/assets/8c042008-44af-45ff-a559-aab2575acafc)

**Notice** the error message that the head command displays. This is because the sysadmin user has no rights to view this file. The root user, however, can display this file.

Type the same command using sudo. 

sudo head /etc/shadow

![Image](https://github.com/user-attachments/assets/365ae035-b246-4047-b35f-c9a1b7317cb7)

The system will prompt for the current user's password, not the root password. If the current user is part of the sudo group, the command will be executed.

By default on many Ubuntu systems, sudo commands entered after the first sudo command will be executed as root without being prompted for a password for the next 15 minutes. Other systems may have different timeouts.

---

### 2. User Accounts
In this task, you will learn about user accounts and the files and commands that display user account information.

User and system accounts are defined in the /etc/passwd and /etc/shadow files. View the first ten lines from the /etc/passwd file. While the passwd file contains general information about a user such as username, UID, GID, home directory and login shell, the modern shadow file has additional details including encrypted password and password policy:

head /etc/passwd

![Image](https://github.com/user-attachments/assets/6e3753f8-aeb2-4b08-9b2a-d232d22d5958)

**Notice** that this file contains a colon delimited database of all user and system accounts available on this system.
User accounts are assigned to users, to allow them access to the operating system. The sysadmin account that you used to log in to the system is a typical user account.
System accounts are used by the operating system or services running processes on it to perform background functions. These accounts often need access to hardware or system files that normally would only be available to the root user. The default permissions for these accounts normally give access to just the sensitive areas needed rather than the broad access of a root or administrator account, thereby limiting the damage that a compromised service account could cause. System accounts are never used directly by regular users.

Use the grep command to view the record for your sysadmin account:

grep sysadmin /etc/passwd

![Image](https://github.com/user-attachments/assets/b2ea37fa-0f8d-4cff-b8f1-7b6f50b3b911)

**By using the grep command, the output only includes the account information for that one username.**

---

### 3. Passwords
The /etc/shadow file contains information about users’ passwords. In this exercise you will use several commands to view the data in this file.

Try to view the first few lines of /etc/shadow file, a file that contains users' encrypted passwords and information about aging them:

head -3 /etc/shadow

![Image](https://github.com/user-attachments/assets/0167a349-dbdb-4cb4-aa35-f32ff5447e45)

**Notice** the error message that the head command displays. This is because the sysadmin user has no rights to view this file. The root user, however, can display this file.

**Notice** that the permissions on the /etc/shadow file indicate that only members of the shadow group have permission to view the file:

ls -l /etc/shadow

![Image](https://github.com/user-attachments/assets/376d9bfe-69d2-4b95-855a-97fe40f92eb3)

**Keep in mind that the root user can view any file. This is due to the root account having special privileges that transcend regular file permissions.**

Use the sudo command to view the first few lines of the /etc/shadow file. Provide the password of the sysadmin user, netlab123, when prompted.

sudo head -3 /etc/shadow

![Image](https://github.com/user-attachments/assets/0b1006c1-3ba1-47bf-833b-acb7acca3862)

**Important**

The password that you provided was for your sysadmin account, not the root account. Once sudo has been configured for your account, you don't need to know the root password to run sudo commands as the root user.

Another way to retrieve the account information for a user is by running the following command: getent passwd username. The getent command has the advantage over the grep command as it is also able to access user accounts that are not defined locally. In other words, the getent command is able to get user information for users who may be defined on network directory servers such as LDAP, NIS, Windows Domain, or Active Directory Domain servers.

Use the getent command to retrieve the information about the sysadmin:

getent passwd sysadmin

![Image](https://github.com/user-attachments/assets/f4083085-84ff-4b85-89c3-9b0a8e3eaef4)

**Note**

In this case, we don't have any network accounts, so the output displayed is just like looking at the /etc/passwd file.
The colon delimited /etc/passwd file has the following fields:

name:password:UID:GID:Comment:directory:shell
A breakdown of these fields:

**Name**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

**Password Placeholder**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

**User ID**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

**Primary Group ID**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

**Comment**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

**Home Directory**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

**Shell**

sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash


You can view the documentation of the fields in the /etc/passwd file with the following command:

man 5 passwd

![Image](https://github.com/user-attachments/assets/15d5f4c0-27ad-47a2-bf12-f45cf217b2d5)

**Important**
Remember while viewing a man page, press Enter to move forward line by line, Space page by page and q to quit.

---

### 4. Account Information

You can view account information for your account, or a specified user account, using the id command:

id
id root

![Image](https://github.com/user-attachments/assets/920e7982-2a31-4573-b03e-5608078aa4f9)

![Image](https://github.com/user-attachments/assets/1cb5f414-23d9-495e-b16d-1419aabf8da3)


**Note**

The file /etc/group, together with /etc/passwd, determines your group memberships. Your default primary group is determined by matching your GID found in /etc/passwd to the GID defined for a group in the /etc/group. Any secondary group memberships are defined in the /etc/group file.
The format of entries in the /etc/group file for each line is:
group_name:password:GID:user_list



### 5. Who is On the System
In this task, you will execute some commands to see who is logged into the system.

Use the who command to get the current list of users on the system:

who

![Image](https://github.com/user-attachments/assets/db936742-fd41-42f5-b09b-66c4f20ca4b5)

The output of the who command has four columns:

**Username**

sysadmin console     Apr 11 14:32
This column indicates the name of the user who is logged in.

**Terminal**

sysadmin console     Apr 11 14:32
This column indicates which terminal window the user is working in.

**Date**

sysadmin console     Apr 11 14:32
This column indicates when the user logged in.

**Host**

Although there is no output for the fourth column in this case, it can be the name or IP address of a local or remote host.


Use the w command to get a more detailed view of the users who are currently on your system:

w

![Image](https://github.com/user-attachments/assets/f318aba2-d32a-4d30-8efc-982ff4453324)

Output from the w command displays a summary of how long the system has been running, how many users are logged in and the system load averages for the past 1, 5, and 15 minutes.
Also displayed is an entry for each user with their login name, tty name (terminal name), host, login time, idle time, JCPU (CPU time used by background jobs), PCPU (CPU time used by the current process) and what is executing on the current command line.

---

### 6. Viewing Login History
The last command reads the entire login history from the /var/log/wtmp file and displays all logins and reboot records by default.

Use the last command to view the /var/log/wtmp file which keeps a log of all users who have logged in and out the system.

last

![Image](https://github.com/user-attachments/assets/e1efd468-ea54-4736-95d8-fc732be56b54)

---
