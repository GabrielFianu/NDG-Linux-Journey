
# Creating Users and Groups. 

## Introduction
By performing this lab, students will learn how to create a new user account, establish the initial password for this account, and make other modifications such as making the new user a member of a secondary group. 
You will perform the following tasks:

Create a new group with the groupadd command
Make changes to groups using the groupmod command
Create a new user with the useradd command
Set and reset a user's password with the passwd command
Make changes to the user account with the usermod command

---

### 1. Create a new group with the groupadd command

In this task, you will create group and user accounts.
Group accounts can be helpful to use in order to be able to assign permissions on files shared by a group of users.
In this lab, you will manage local group and user accounts.

In order to administer the user and group accounts, you will want to switch users to the root account with the following command. Provide the root password netlab123 when prompted.

su -

![Image](https://github.com/user-attachments/assets/d12bc85c-597a-4d1f-ab48-28feda91e8b6)

**Use the groupadd command to create groups called research and sales**

groupadd -r research

![Image](https://github.com/user-attachments/assets/264ce7cc-cb8b-4fdc-8e24-45c1ea82093b)

![Image](https://github.com/user-attachments/assets/c2d4bec9-8e41-4cbe-8bfb-f1c6411143a1)

The research and sales groups that were just added were added in the reserved range (between 1-999) because the -r option was used. With this option, Group Identifiers (GIDs) are automatically assigned with a value of less than the lowest normal user UID. The groupadd command modifies the /etc/group file where group account information is stored.
The groupmod command can be used with a -n option to change the name of either of these groups or with the -g option in order to change the GID for either of the groups. The groupdel command can be used to delete either of the groups, as long as neither of them have been made the primary group for a user.


**Use the getent command to retrieve information about the new research group**

getent group research

Your output should appear similar to the example above although the GID that was assigned may be different. Now that the research group has been created, existing or new users can be made members of the group.

![Image](https://github.com/user-attachments/assets/bd6cf4f7-1aea-4177-a350-f405c4903bd7)

**Use the grep command to retrieve information about the new sales group**

grep sales /etc/group

![Image](https://github.com/user-attachments/assets/95b82541-2841-437b-b66a-f677dcbd7270)

Your output should appear similar to the example above although the GID that was assigned may be different. Now that the sales group has been created, existing or new users can be made members of this group.

---

### 2. Make changes to groups using the groupmod command

**Use the groupmod command with the -n option to change the name of the sales group**

groupmod -n clerks sales

Now use the groupmod command with the -g option to change the GID for the group.

![Image](https://github.com/user-attachments/assets/cbf226df-ddbe-47e4-ba7f-dace286486ad)

groupmod -g 10003 clerks

![Image](https://github.com/user-attachments/assets/4092313a-725b-4c82-9077-979d3c4309a5)

grep clerks /etc/group

![Image](https://github.com/user-attachments/assets/fb9181a4-12c4-4931-a8e6-0bc5e8ea3b3d)

**Note** that any files that had been in the sales group will now have no group name and will now be orphaned files.


**Delete the clerks group using the groupdel command along with the name of the group**

groupdel clerks
root@localhost:~# groupdel clerks
Use the grep command to verify that the clerks group has been removed:

![Image](https://github.com/user-attachments/assets/0127cb01-5233-4415-9a6e-ba2586128393)

root@localhost:~# grep clerks /etc/group
root@localhost:~#

![Image](https://github.com/user-attachments/assets/8743928d-a7b0-4b0f-b2a8-6b81fa276284)

**Important**
If you decide to delete a group with the groupdel command, be aware that any files that are owned by that group will also become orphaned.

---

### 3. User Configuration

User configuration begins with properly configuring the groups that users will be placed in.

View the default values used by the useradd command using the -D option:

useradd -D

![Image](https://github.com/user-attachments/assets/a2892b7d-b0b4-4e87-b476-79bffaff0221)

The SKEL value provides administrators with an easy way to populate a new user account with key configuration files. It determines which skeleton directory will have its contents copied into the new user’s home directory. The -k option on the useradd command allows a different SKEL directory than the default to be used when creating a new user account. This is useful because most systems have users that need access to different resources as appropriate to their job functions.
The SKEL value provides administrators with an easy way to populate a new user account with key configuration files. It determines which skeleton directory will have its contents copied into the new user’s home directory. The -k option on the useradd command allows a different SKEL directory than the default to be used when creating a new user account. This is useful because most systems have users that need access to different resources as appropriate to their job functions.
Set the INACTIVE parameter to allow users with expired passwords to log in for up to thirty days before their accounts are disabled, then view the new default values. The -D option to the useradd command will allow you to view or change some of the default values used by the useradd command.

In the example below, the -D option specifies changes to the default values used when creating a new user. The -f 30 option specifies that users who have expired passwords can still log in for up to thirty days before their accounts are inactivated. Using the -D option by itself displays the current defaults, which have been changed by the previous command.

useradd -D -f 30
useradd -D

![Image](https://github.com/user-attachments/assets/a815cb1d-1ee6-4e34-b49e-772db0245a76)

![Image](https://github.com/user-attachments/assets/9328300e-857d-43a2-a6f1-7c1086c8080b)

Modify the CREATE_MAIL_SPOOL value in the /etc/default/useradd file using the nano text editor:

nano /etc/default/useradd
root@localhost:~# nano /etc/default/useradd

![Image](https://github.com/user-attachments/assets/44135f9f-f2e3-4fc0-a1cd-442ae22efc4d)

![Image](https://github.com/user-attachments/assets/6862f47b-2aad-44e9-9e0f-442fea739f11)

Press the down arrow ↓ key to scroll to the bottom of the file:

On the CREATE_MAIL_SPOOL=no line, backspace over the no and type yes:

![Image](https://github.com/user-attachments/assets/0c104e33-af6a-4a96-96f6-38a26ad395f8)

Press Ctl + X to exit and type Y. Press Enter to save your changes then type useradd -D at the prompt to confirm the new setting:

useradd -D

![Image](https://github.com/user-attachments/assets/aac3c25e-187a-416c-a8fd-0b370d4f0272)

The useradd command will now create a mail spool file.

---

### 4. Creating new user

Create a new user named student who is a secondary member of the research group and a primary member of their own private group. Use a comment of Linux Student that will appear as the full name of the user when they do a graphical login. Make sure that their home directory will be created by specifying the -m option. Then use grep to verify the new user and their group memberships:

useradd -G research -c 'Linux Student' -m student
grep student /etc/passwd
grep student /etc/group

![Image](https://github.com/user-attachments/assets/754b6373-244f-48be-8305-2a80c161083a)

![Image](https://github.com/user-attachments/assets/55e48459-60af-4593-a34d-501e6ba565fa)

![Image](https://github.com/user-attachments/assets/9d89665a-79e3-42e0-9dee-921e35df563c)

The user's account information is stored in the /etc/passwd and /etc/shadow files. The user's group information can be found in the /etc/passwd and /etc/group files.

**Use the usermod command to add the research group as a secondary group for the sysadmin user**

usermod -aG research sysadmin

![Image](https://github.com/user-attachments/assets/443a0fb1-a607-44dc-a251-bf376226a32b)

Users who are actively logged into the system will not be able to use any new group memberships until the next time they log into the system.

**Using the getent command, view the research group members again**

getent group research

![Image](https://github.com/user-attachments/assets/e8063474-eb14-4683-8c25-d370dad094e3)

**Use getent to show the student group:**

getent group student

![Image](https://github.com/user-attachments/assets/5f4902c5-d5ae-484a-9d27-d493292a8231)

Next, use getent to show the passwd and shadow databases for the student user:

getent passwd student
getent shadow student

![Image](https://github.com/user-attachments/assets/7251a2ad-010e-4d10-81ef-4c9ff8e0bbe1)

![Image](https://github.com/user-attachments/assets/91b2a5ba-4446-4c70-98f0-194112770fd7)

The output should now show that both sysadmin and student are secondary members of the research group.
The GID of the student group matches the fourth field of the passwd information for the student user. This is what makes the student a primary member of the student group.
Finally, the ! appearing in the second password field of the shadow file, shows that the password for the student has not been set.

---

### 5. Set and Reset user password

**Use the passwd command to set the password.** 
Enter the password twice then view the shadow file entry for the student user again:

passwd student

![Image](https://github.com/user-attachments/assets/c3427fcd-cd9d-49f5-a2b3-a9cb4924daba)

**Note**
No characters will appear when typing the password.

The output from the /etc/shadow file now shows an encrypted password in the second field:

getent shadow student

![Image](https://github.com/user-attachments/assets/f763cffa-7ee9-4d33-a321-6de95bcc8e36)

Just because a user has a password doesn't mean that they have ever logged into the system. Use the last command to see if the student user has ever logged in:

**last**

![Image](https://github.com/user-attachments/assets/6c0dd64f-d5c6-463a-a65e-7ef212aabbe0)

last student

![Image](https://github.com/user-attachments/assets/0156668c-2665-46a7-950b-d8ffa8c55ebf)


The output of the last command should show that the sysadmin user has logged in before, but not the student user. There is also a lastb command, which works similar to the last command except that it shows "bad" or failed login attempts.
If you no longer wanted the student user to have access to the system, then the usermod -L student command could be used to "lock" the account. The account could be unlocked with the usermod -U student command.

A more permanent solution to preventing access to the student account would be to delete the account with either the userdel student or userdel -r student commands. Using the -r option with the userdel command removes the user's home directory and mail, in addition to deleting the user's account.

Delete the student account and remove the user's home directory:

userdel -r student

![Image](https://github.com/user-attachments/assets/3c5b9ee0-9f57-45fd-9ad0-359a7f41e9a4)

Use the grep command to verify the student user has been removed.

grep student /etc/group 

![Image](https://github.com/user-attachments/assets/09e59abb-ab8b-4daf-aae1-862236d25ed8)
