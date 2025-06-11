# Navigating the Filesystem

## Introduction
This exercise  will help you to learn how to navigate and manage files and directories by perform the following tasks:

Navigate home and system directories
List files and directories

**Note:**
File and directory names in Linux are case-sensitive. This means that a file named ABC is not the same as a file named abc.

---

### 1. Files and Directories
In this task you will explore the concepts of files and directories.

Type the following command to print the working directory:
The working directory is the directory that your terminal window is currently "in". This is also called the current directory. 

pwd

![Image](https://github.com/user-attachments/assets/725b85a0-4ef7-455d-8dbe-94ecc12b581c)

The output of the pwd command (/home/sysadmin in the example above) is called the path. The first slash represents the root directory, the top level of the directory structure.
In the output above, home is a directory under the root directory and sysadmin is a directory under the home directory.

When you first open a terminal window, you will be placed in your home directory. This is a directory where you have full access and other users normally have no access by default. 
To see the path to your home directory, you can execute the following command to view the value of the HOME variable:

echo $HOME

![Image](https://github.com/user-attachments/assets/4a3c8663-af25-4391-afa1-841b1ab8fff7)

You can use the cd command with a path to a directory to change your current directory. 

Type the following command to make the root directory your current working directory and verify with the pwd command:

cd /
pwd

![Image](https://github.com/user-attachments/assets/cf1f5f80-f76b-4caa-8138-aa00ce40ab69)

![Image](https://github.com/user-attachments/assets/a0c27cb2-7aeb-468d-8b2a-3980e109230a)

To change back to your home directory, the cd command can be executed without a path. 
Change back to your home directory and verify by typing the following commands:

cd
pwd

![Image](https://github.com/user-attachments/assets/4c466c6f-9cff-440d-8c49-d4f545218161)

**Notice** the change in the prompt. The tilde ~ character represents your home directory. This part of the prompt will tell you what directory you are currently in.

The cd command may be entered with a path to a directory specified as an argument. Execute the cd command with the /home directory as an argument by typing the following:

cd /home
pwd

![Image](https://github.com/user-attachments/assets/d2a61707-7041-45a0-b778-af9c7a77f287)

![Image](https://github.com/user-attachments/assets/e05f4e6b-8134-46ba-a292-0bc867c19204)


When the path that is provided as an argument to the cd command starts with the forward slash /, that path is referred to as an “absolute path”. 
Absolute paths are always complete paths from the root directory to a subdirectory or file.


Change back to your home directory, using the cd command with the tilde ~ as an argument:

cd ~
pwd

![Image](https://github.com/user-attachments/assets/7de17c94-d77f-4c17-b048-b8f6c088f22f)

![Image](https://github.com/user-attachments/assets/6b6be02d-cf04-46ea-a5be-eca96525bb85)


When the path that is provided as an argument to the cd command starts with a tilde ~ character, the terminal will expand the character to the home directory of a user with an account on the system.

If either no other characters or a forward slash follows the tilde, then it will expand to the home directory of the user currently active in the shell.

If a user name immediately follows the tilde character, then the shell will expand the tilde and user name to the home directory of that user name. For example, ~bob would be expanded to /home/bob.

Paths that start with a tilde are considered absolute paths because after the shell expands the tilde path, an absolute path is formed.


Use the echo command below to display some other examples of using the tilde as part of the path:

echo  ~ ~sysadmin ~root ~mail ~nobody

![Image](https://github.com/user-attachments/assets/4cb4a785-eb8f-436c-b3e4-9a67bdcf9cc6)

Attempt to change to the home directory of the root user by typing the following command:

cd ~root

![Image](https://github.com/user-attachments/assets/180f6f71-069c-4ae8-b2f3-cb8ef554ac51)


**Notice** the error message; it indicates that the shell attempted to execute cd with /root as an argument but it failed due to permission being denied. 

Using an absolute path, change to the /usr/bin directory and display the working directory by using the following commands:

cd /usr/bin
pwd

![Image](https://github.com/user-attachments/assets/4da1ba5f-e364-43a6-9fcb-7180d90c56c9)

![Image](https://github.com/user-attachments/assets/0698f2ee-00b4-4112-82bd-7a809ffc5413)


Use an absolute path to change to the /usr directory and display the working directory by issuing the following commands:

cd /usr
pwd

![Image](https://github.com/user-attachments/assets/3fbf65c8-7a43-429c-a6c7-a0dc2f3ef3a4)

![Image](https://github.com/user-attachments/assets/a2e916fe-c986-457b-950e-4e24505eadb0)

Use an absolute path to change to the /usr/share/doc directory and display the working directory by issuing the following commands:

cd /usr/share/doc
pwd

![Image](https://github.com/user-attachments/assets/994ced44-e277-4789-975d-adc957a38cc5)

![Image](https://github.com/user-attachments/assets/1ef55878-2694-4311-8ec2-6ea419ae37c3)

Absolute vs. Relative pathnames

Suppose you are in the /usr/share/doc directory and you want to go to the /usr/share/doc/bash directory. Typing the command cd /usr/share/doc/bash results in a fair amount of typing. In cases like this, you want to use relative pathnames.

With relative pathnames you provide "directions" of where you want to go from the current directory. The following examples will illustrate using relative pathnames.


Using a relative path, change to the /usr/share/doc/bash directory and display the working directory by issuing the following commands:

cd bash
pwd

![Image](https://github.com/user-attachments/assets/8082c552-eca8-4fac-b44c-ae5521f9d9df)


**Note**

If there wasn't a bash directory under the current directory, the previous command would fail.

Use a relative path to change to the directory above the current directory:

cd ..
pwd

![Image](https://github.com/user-attachments/assets/ad8ff917-c30a-42b2-96e1-5dffa5ddb740)

![Image](https://github.com/user-attachments/assets/226cb287-dd70-4a57-b6a5-5ed3c0659cdb)


The .. represents one level above your current directory location.

Use a relative path to change up one level from the current directory and then down into the dict directory:

cd ../dict
pwd

![Image](https://github.com/user-attachments/assets/306296a7-dc65-497a-8dbe-c445a3f94393)

![Image](https://github.com/user-attachments/assets/796a1078-181f-49c0-9bba-1a08790f819e)

---

### 2. Listing Files and Directories
In this task, you will explore how to list files and directories.

To list the contents of the current directory, use the ls command:

cd
ls

![Image](https://github.com/user-attachments/assets/8fecc73e-14e8-4d76-be74-42a4cf1a4362)

![Image](https://github.com/user-attachments/assets/cf717ac3-9ba8-427d-8b94-66b7ebc35878)


In the output of the previous ls command, the file names were placed in a light blue color. This is a feature that many distributions of Linux automatically provide through a feature called an alias.
The color indicates what type the item is. The following table describes some of the more common colors:

Color		Type of File
Black 
or White	Regular file
Blue		Directory file
Cyan		Symbolic link file (a file that points to another file)
Green		Executable file (a program)


Not all files are displayed by default. There are files, called hidden files, that are not displayed by default. To display all files, including hidden files, use the -a option to the ls command:

ls -a

![Image](https://github.com/user-attachments/assets/389141fc-0ff7-401b-bd75-a13104e11efe)

The names of hidden files begin with a period (a dot character). Typically these files and often directories are hidden because they are not files you normally want to see.
For example, the .bashrc file shown in the example above contains configuration information for the bash shell. This is a file that you normally don't need to view on a regular basis.
Two important "dot files" exist in every directory: . (which represents the current directory) and .. (which represents the directory above the current directory).


By itself, the ls command just provided the names of the files and directories within the specified (or current) directory. Execute the following command to see how the -l option provides more information about a file:

ls -l /etc/hosts

![Image](https://github.com/user-attachments/assets/73516121-d29c-4797-b61c-bbf488b935d5)

So, what does all of this extra output mean? The following table provides a brief breakdown of what each part of the output of ls -l means:

-	The first character, a - in the previous example, indicates what type of "file" this is. A -character is for a plain file while a d character would be for a directory.
rw-r--r--	This represents the permissions of the file. Permissions are discussed in a later lab.
1	This represents something called a hard link count (discussed later).
root	The user owner of the file.
root	The group owner of the file.
150	The size of the file in bytes
Jan 22 15:18	The date/time when the file was last modified.


Sometimes you want to see not only the contents of a directory, but also the contents of the subdirectories. You can use the -R option to accomplish this:

ls -R /etc/udev

![Image](https://github.com/user-attachments/assets/eb2154b2-2ce7-4949-9b8c-44fbab24e77b)

The -R option stands for "recursive". All of the files in the /etc/udev directory will be displayed as well as all of the files in each subdirectory, in this case the rules.d subdirectory.

Be careful of the -R option. Some directories are very, very large!


You can use file globbing (wildcards) to limit which files or directories you see. For example, the * character can match "zero or more of any characters" in a filename. Execute the following command to display only the files that begin with the letter s in the /etc directory:

ls -d /etc/s*

![Image](https://github.com/user-attachments/assets/4413ecd2-2bb3-49e5-8666-dbf0e1f06034)


**Note** 
that the -d option prevents files from subdirectories from being displayed. It should always be used with the ls command when you are using file globbing.



The ? character can be used to match exactly 1 character in a file name. Execute the following command to display all of the files in the /etc directory that are exactly four characters long:

ls -d /etc/????

![Image](https://github.com/user-attachments/assets/5c350a40-cd5e-4973-8d6d-f749a0f458a9)

By using square brackets [ ] you can specify a single character to match from a set of characters. Execute the following command to display all of the files in the /etc directory that begin with the letters a, b, c or d:

ls –d /etc/[abcd]*

![Image](https://github.com/user-attachments/assets/bfd13600-dd1e-49e1-9c31-88b6e42a3f99)


