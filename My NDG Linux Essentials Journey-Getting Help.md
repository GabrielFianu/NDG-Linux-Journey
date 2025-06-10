# Getting Help. 

## Introduction
This will help you to learn how to get help on commands and find files by performing the following tasks:

Use several help systems to get help for commands.
Learn how to locate commands.
Execute commands in the bash shell by typing the command and then pressing the Enter key. For example, type the following command to display today's date:
date

---

### 1. Help systems

** man command**
To learn more about commands, access the manual page for the command with the man command. For example, execute the following command to learn more about the date command:

man date

![Image](https://github.com/user-attachments/assets/6afd075f-3294-4d3b-b36d-07310a30a4c7)
![Image](https://github.com/user-attachments/assets/2837ccd4-52db-4f16-a53a-74fbb7428c38)

**Note**

Documents that are displayed with the man command are called "Man Pages".

If the man command can find the manual page for the argument provided, then that manual page will be displayed using a command called less. The following table describes useful keys that can be used with the less command to control the output of the display:

Key	Purpose
H or h	Display the help
Q or q	Quit the help or manual page
Spacebar or f or PageDown	Move a screen forward
b or PageUp	Move a screen backward
Enter or down arrow	Move down one line
Up arrow	Move up one line
/ followed by text to search	Start searching forward
? followed by text to search	Start searching backward
n	Move to next text that matches search
N	Move to previous matching text

Type the letter h to see a list of movement commands. After reading the movement commands, type the letter q to get back to the document.

![Image](https://github.com/user-attachments/assets/4efea7db-1966-4118-840f-6c95156a4d8a)

Note that the man pages might be a bit of a mystery to you now, but as you learn more about Linux, you will find they are a very valuable resource.
Searches are not case sensitive and do not "wrap" around from the bottom to top, or vice versa. Start a forward search for the word "file" by typing:

/file
Note that what you are typing will appear at the bottom left portion of the screen.

![Image](https://github.com/user-attachments/assets/c8811800-85b3-4193-8595-9b8017599df7)

Press Enter to search the document for the search string (file).

![Image](https://github.com/user-attachments/assets/7bb1b2f5-4615-4376-89ca-ca2390a2c9e0)

Notice that the text matching the search is highlighted. You can move forward to the next match by pressing n. Also try moving backwards through the matches by pressing N:
Use the movement commands previously described (such as using the spacebar to move down one screen) to read the man page for the date command. When you are finished reading, type q to exit the man page.
In some cases you may not remember the exact name of the command. In these cases you can use the -k option to the man command and provide a keyword argument. For example, execute the following command to display a summary of all man pages that have the keyword "password" in the description:

The -k option to the man command will often produce a huge amount of output. We will cover a technique in a later lab to either limit this output or allow you to easily scroll through the data. For now, you can scroll using your mouse in the terminal window to move the display up and down as needed.

![Image](https://github.com/user-attachments/assets/8812617b-1368-47f3-ad75-95df01c03e35)


**Note** that the apropos command is another way of viewing man page summaries with a keyword. Type the following command:

![Image](https://github.com/user-attachments/assets/ff1a24d9-a764-4710-9528-9cca94461941)

**Note**
There is no difference between man -k and the apropos command.


There are often multiple man pages with the same name. For example, the following command shows three pages for passwd. Execute the following command to view the man pages for the word passwd:

man -f passwd

![Image](https://github.com/user-attachments/assets/054d592c-90f2-47c8-a7c0-f5cb15c07049)

The fact that there are different man pages for the same "name" is confusing for many beginning Linux users. Man pages are not just for Linux commands, but also for system files and other "features" of the Operating System. Additionally, there will sometimes be two commands with the same name, as in the example provided above.

The different man pages are distinguished by "sections". By default there are nine sections of man pages:

Executable programs or shell commands
System calls (functions provided by the kernel)
Library calls (functions within program libraries)
Special files (usually found in /dev)
File formats and conventions, e.g. /etc/passwd
Games
Miscellaneous (including macro packages and conventions), e.g. man(7)>, groff(7)
System administration commands (usually only for root)
Kernel routines
When you type a command such as man passwd, the first section is searched and, if a match is found, the man page is displayed. The man -f passwd command that you previously executed shows that there is a section 1 man page for passwd: passwd (1). As a result, that is the one that is


To display a man page for a different section, provide the section number as the first argument to the man command. For example, execute the following command:


man 5 passwd

![Image](https://github.com/user-attachments/assets/18923f9f-ff4a-4af7-aa3c-794553fe3c11)
![Image](https://github.com/user-attachments/assets/47c879fd-2d5a-4ae7-b2d5-8d0f8a2ac731)

**Type q to return to the system prompt.**


Instead of using man -f to display all man page sections for a name, you can also use the whatis command:

**whatis passwd**

![Image](https://github.com/user-attachments/assets/a59af6d5-dc96-4604-85ce-85c1a65bf961)

**Note**
There is no difference between man -f and the whatis command.

Almost all system features (commands, system files, etc.) have man pages. Some of these features also have a more advanced feature called info pages. For example, execute the following command:

**info date**

![Image](https://github.com/user-attachments/assets/3f86cf02-cfe2-4152-addc-4be2e2ef3adf)
![Image](https://github.com/user-attachments/assets/22b2b531-89bc-4c2f-ade9-7ee8ba04ada2)


Many beginning Linux users find info pages to be easier to read. They are often written more like "lessons" while man pages are written purely as documentation.
While viewing the info page from the previous step, type Shift and the letter h to see a list of movement commands. Note that they are different from the movement commands used in man pages. After reading the movement commands, type the letter l (lowercase L) to return to viewing the document.

Use the movement commands to read the info page for the date command. When you are done, put your cursor anywhere on the line that reads *Examples of date:: and then press the Enter key. A new document will be displayed that shows examples of date.
Type the l key to return to the previous screen. When you are finished reading, type q to exit the info page.

Another way of getting help is by using the --help option to a command. Most commands allow you to pass an argument of --help to view basic command usage:

**date --help**

![Image](https://github.com/user-attachments/assets/35ffe3c7-0f79-4adf-b4a8-df5f54b70cd1)
![Image](https://github.com/user-attachments/assets/c65b37e3-af62-40d9-9560-a6d7dfdb0795)
Some system features also have more detailed help documents located in the /usr/share/doc directory structure. Execute the following command to view the contents of this document:

ls /usr/share/doc
![Image](https://github.com/user-attachments/assets/030fef0b-062e-4c44-bd5a-c591f34d75d7)

Note that in almost all cases, the man pages and info pages will provide you with the information that you need. However, if you need more in-depth information (something that system administrators sometimes need), then you may find this information in the files located in the /usr/share/doc

---

### 2. Finding Files
In this task, we will explore how to search for a file on the system. This is useful to know in situations when you can't find a file on the system, either one that you created or one that was created by someone else.

An easy way to search for a file is to use the locate command. For example, you can find the location of the crontab file by executing the following command:

**locate command**
locate crontab

![Image](https://github.com/user-attachments/assets/022dc6bd-cd46-44ec-bc70-5c9c634abcef)

**Note** that the output from the previous example includes files that have crontab as part of their name. To find files that are just named crontab, use the following command:

locate -b "\crontab"
![Image](https://github.com/user-attachments/assets/7d93966d-ca58-49d8-bc19-9c3a294efc66)

**Note:** The locate command makes use of a database that is traditionally updated once per day (normally in the middle of the night). This database contains a list of all files that were on the system when the database was last updated.

As a result, any files that you created today will not normally be searchable with the locate command. If you have access to the system as the root user (the system administrator account), you can manually update this file by running the updatedb command. Regular users cannot update the database file.

Another possible solution to searching for "newer" files is to make use of the find command. This command searches the live filesystem, rather than a static database. The find command isn't part of the Linux Essentials objectives for this lab, so it is only mentioned here. Execute man find if you want to explore this command on your own.



You may just want to find where a command (or its man pages) is located. This can be accomplished with the **whereis** command:

![Image](https://github.com/user-attachments/assets/966200cf-7354-40cd-b5c7-a6d691f56e5a)

The **whereis** command does not search for just any file, only for commands and man pages.

Recall from earlier that there is more than one passwd man page on the system. This is why you see multiple file names and man pages (the files that end in .gz are man pages) when you execute the previous command.
