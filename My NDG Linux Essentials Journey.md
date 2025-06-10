# Command Line Skills

## Introduction

In this task, we will access the Command Line Interface (CLI) for Linux to explore how to execute basic commands and what affects how they can be executed.

---

### 1. whoami

The output of the whoami command, sysadmin, displays the user name of the current user. 
This command could be used to obtain this information in a situation when the prompt did not contain this information
![Image](https://github.com/user-attachments/assets/195dd680-aaca-44dd-8ce4-088804775399)

---

### 2. uname
This command displays information about the current system. To be able to see the name of the kernel you are using, type the following command into the terminal:
uname
![Image](https://github.com/user-attachments/assets/17f6990f-0a50-4c3e-989f-95d67a1c6e49)

---

### 3. Options 

In Linux, options can sometimes also be given by two hyphen characters followed by a word, or hyphenated word; for example: --nodename.

Execute the uname command again twice in the terminal, once with the option -n and again with the option --nodename. 

uname -n
uname --nodename
Your output should be similar to the following:
![Image](https://github.com/user-attachments/assets/f7f0494f-3e6a-46b1-91fa-7cd8680e0788)
![Image](https://github.com/user-attachments/assets/50681b25-1907-479f-9dfb-d55486c87103)

---

### 4. pwd
The pwd command is used to display your current "location" or current "working" directory. Type the pwd command to display the working directory.

pwd

pwd stands for "print working directory". 

![Image](https://github.com/user-attachments/assets/6333d531-db41-4797-a49c-1e81f6d02521)

---

### 5. Command History
The Bash shell maintains a history of the commands that you type. Previous commands can be easily accessed in this history in several ways.
The first and easiest way to recall a previous command is to use the up arrow key. Each press of the up arrow key goes backwards one command through your command history. If you accidentally go back too far, then the down arrow key will go forwards through the history of commands.
When you find the command that you want to execute, you can use the left arrow keys and right arrow keys to position the cursor for editing. Other useful keys for editing include the Home, End, Backspace and Delete keys.

Another way to use your command history is to execute the history command to be able to view a numbered history list. The number listed to the left of the command can be used to execute the command again. 
The history command also has a number of options and arguments which can manipulate which commands will be stored or displayed.

Execute  new commands (echo and date) and then execute the history command:
echo Hi
date
history

![Image](https://github.com/user-attachments/assets/27d7dc83-8b96-498f-b699-e4c49d89c531)
![Image](https://github.com/user-attachments/assets/174ee67a-0c7d-41be-bea7-641ae5b3f26d)

**Remember**
The date command will print the time and date on the system. The clear command clears the screen.


To view a limited number of commands, the history command can take a number as a parameter to display exactly that many recent entries. Type the following command to display the last five commands from your history:

history 5
![Image](https://github.com/user-attachments/assets/69307dec-c2ff-4ca0-ab70-9a701d4febb7)

To execute a command again, type the exclamation point and the history list number. For example, to execute the 9th command in your history list, you would execute the following:

!9
![Image](https://github.com/user-attachments/assets/a09a0c26-9e32-4e21-b286-478dfea9da91)

Next, experiment with accessing your history using the up arrow keys and down arrow keys. Keep pressing the up arrow key until you find a command you want to execute. If necessary, use other keys to edit the command and then press Enter to execute the command.

---

### 6. Shell Variables
Shell variables are used to store data in Linux. This data is used by the shell itself as well as by programs and users.

**echo command**
The echo command can be used to print text and the value of a variable, and to show how the shell environment expands metacharacters. 
Type the following command to have it output literal text:

echo Hello Student
![Image](https://github.com/user-attachments/assets/b942dd68-91ea-407d-a2e8-096875e64c2a)

**Environment variables**
Environment variables are available system-wide. The system automatically recreates environment variables when a new shell is opened. Examples include the PATH, HOME, and HISTSIZE variables. The HISTSIZE variable defines how many previous commands to store in the history list. 
In the example below, the command will display the value of the HISTSIZE variable:

![Image](https://github.com/user-attachments/assets/9efd1713-a839-4f44-8c82-0245fe7f111e)

Type the following command to display the value of the PATH variable:

echo $PATH
Your output should be similar to the following:
![Image](https://github.com/user-attachments/assets/cb5668d8-a77b-4e49-9ca9-02e4a4dfd08d)

The PATH variable is displayed by placing a $ character in front of the name of the variable.

This variable is used to find the location of commands. Each of the directories listed above are searched when you run a command. 
For example, if you try to run the date command, the shell will first look for the command in the /home/sysadmin/bin directory and then in the /usr/local/sbin directory and so on. Once the date command is found, the shell "runs it”.


**which command**
Use the which command to determine if there is an executable file, in this case named date, that is located within a directory listed in the PATH value:

which date

The output of the which command tells you that when you execute the date command, the system will run the command /bin/date. The which command makes use of the PATH variable to determine the location of the date command.
![Image](https://github.com/user-attachments/assets/16503b95-22f2-42c3-b813-577ab5aa24ae)

---

## 7. Command Types
In this section we will learn about the four types of commands used in Linux. Understanding where these commands come from and how they differ allows an administrator to manage the system more effectively.

One way to learn more about a command is to look at where it comes from. The type command can be used to determine information about command type.

**type command**
One way to learn more about a command is to look at where it comes from. The type command can be used to determine information about command type.
type command

![Image](https://github.com/user-attachments/assets/02256a87-157b-43ce-b714-660e89560877)

There are several different sources of commands within the shell of your CLI:

Internal commands are built into the shell itself. A good example is the cd (change directory) command as it is part of the Bash shell. When a user types the cd command, the Bash shell is already executing and knows how to interpret it, requiring no additional programs to be started.

The type command identifies the cd command as an internal command:

External commands are binary executables stored in directories that are searched by the shell. If a user types the ls command, the shell searches through the directories that are listed in the PATH variable to try to find a file named ls that it can execute. Use the which command to display the full path to the ls command.

which ls

![Image](https://github.com/user-attachments/assets/905dc54f-e98e-4ec4-9219-0777a2fb3ed9)

For external commands, the type command displays the location of the command:

![Image](https://github.com/user-attachments/assets/66d69588-1d63-43bf-b738-52dd0b0c1194)

In some cases the output of the type command may differ significantly from the output of the which command:

![Image](https://github.com/user-attachments/assets/66d69588-1d63-43bf-b738-52dd0b0c1194)

Using the -a option of the type command displays all locations that contain the command:

![Image](https://github.com/user-attachments/assets/9fce45f2-f1a9-4f0b-9cd4-9782d64ff482)

---

## 8. alias command
Aliases can be used to map longer commands to shorter key sequences. When the shell sees an alias being executed, it substitutes the longer sequence before proceeding to interpret commands.

To determine what aliases are set on the current shell, use the alias command:

![Image](https://github.com/user-attachments/assets/8b99b604-0840-474b-8660-a70ec4cc2a3b)

---

## 9. Executable program
The final command type is the executable program. These commands invoke programs installed on the system which perform specific tasks. 
When a user types the vi command, the shell uses the PATH file to locate and execute the program. 
Programs like vi are available on just about every Linux distribution; other programs, like vlc (an open source media player often used on Linux desktops), are installed by users or administrators for a specific purpose and will not be listed in the PATH unless they have been installed separately.

type vi
cd /bin
type vlc
cd

![Image](https://github.com/user-attachments/assets/a32002aa-f351-4e14-80c4-9fdfff9414b3)
![Image](https://github.com/user-attachments/assets/07914022-291b-4d43-908f-6800d186b74d)
![Image](https://github.com/user-attachments/assets/374811f3-c936-489a-a1a1-089dc9724d18)
![Image](https://github.com/user-attachments/assets/75d5ba42-45c2-4a90-acf5-687ba7a4610c)


## 10. Quoting
There are three types of quotes used by the Bash shell: single quotes ('), double quotes (") and back quotes (`). These quotes have special features in the Bash shell as described below.

To understand single and double quotes, consider that there are times that you don't want the shell to treat some characters as special. For example, the * character is used as a wildcard. What if you wanted the * character to just mean a literal asterisk?

Single ' quotes prevent the shell from "interpreting" or expanding all special characters. Often single quotes are used to protect a string (a sequence of characters) from being changed by the shell, so that the string can be interpreted by a command as a parameter to affect the way the command is executed.

Double " quotes stop the expansion of glob characters like the asterisk (*), question mark (?), and square brackets ( [] ). Double quotes do allow for both variable expansion and command substitution (see back quotes) to take place.

Back ` quotes cause command substitution which allows for a command to be executed within the line of another command.

When using quotes, they must be entered in pairs or else the shell will not consider the command complete.

While single quotes are useful for blocking the shell from interpreting one or more characters, the shell also provides a way to block the interpretation of just a single character called "escaping" the character. To escape the special meaning of a shell metacharacter, the backslash \ character is used as a prefix to that one character.


**back quotes** `
Execute the following command which uses back quotes ` (found under the ~ character on some keyboards) to execute the date command within the line of the echo command:

echo Today is `date`
![Image](https://github.com/user-attachments/assets/fb48b663-bcc0-45a9-8698-4ea6b6fb62b4)

You can also place $( before the command and ) after the command to accomplish command substitution:

echo Today is $(date)
![Image](https://github.com/user-attachments/assets/517c2f1a-f39e-4ab8-8bfb-5279f841e792)
Why two different methods that accomplish the same thing? Backquotes look very similar to single quotes, making it harder to "see" what a command is supposed to do. 

Originally, shells used backquotes; the $(command) format was added in a later version of the Bash shell to make the statement more visually clear.


If you don't want the backquotes to be used to execute a command, place single quotes around them. Execute the following:

echo This is the command '`date`'
![Image](https://github.com/user-attachments/assets/f14980ad-fbb0-4a5e-a9c5-3b82d5a7da9b)

Double quote " characters don't have any effect on backquote characters. The shell will still use them as command substitution. Execute the following to see a demonstration:

echo This is the command "`date`"
![Image](https://github.com/user-attachments/assets/cf16f3c0-7ed6-4d8d-ac4c-b0f6998c45a3)

Note that you could also place a backslash \ character in front of each backquote character. Execute the following:

echo This is the command \`date\`
![Image](https://github.com/user-attachments/assets/9f461a07-2168-4c12-88c0-6347ca2546bb)

Double quote characters will have an effect on wildcard characters, disabling their special meaning. Execute the following:

echo D*
![Image](https://github.com/user-attachments/assets/610466b5-8975-4e7a-829b-e9d97e983416)
echo "D*"
![Image](https://github.com/user-attachments/assets/f6c33c11-9350-4526-97f0-55d8574ce713)

Important

Quoting may seem trivial and weird at the moment, but as you gain more experience working in the command shell, you will discover that having a good understanding of how different quotes work is critical to using the shell.

---

## 11. Control Statements
Typically, you type a single command and you execute it when you press Enter. The Bash shell offers three different statements that can be used to separate multiple commands typed together.

The simplest separator is the semicolon (;). Using the semicolon between multiple commands allows for them to be executed one right after another, sequentially from left to right.

The && characters create a logical "and" statement. Commands separated by && are conditionally executed. If the command on the left of the && is successful, then the command to the right of the && will also be executed. If the command to the left of the && fails, then the command to the right of the && is not executed.

The || characters create a logical "or" statement, which also causes conditional execution. When commands are separated by ||, then only if the command to the left fails, does the command to the right of the || execute. If the command to the left of the || succeeds, then the command to the right of the || will not execute.

To see how these control statements work, you will be using two special executables: true and false. The true executable always succeeds when it executes, whereas, the false executable always fails. While this may not provide you with realistic examples of how && and || work, it does provide a means to demonstrate how they work without having to introduce new commands.

Execute the following three commands together separated by semicolons:

echo Hello; echo Linux; echo Student
![Image](https://github.com/user-attachments/assets/b3c2f15d-4ccb-45a6-bd01-5ccda8fed9d1)
As you can see the output shows all three commands executed sequentially:


Now, put three commands together separated by semicolons, where the first command executes with a failure result:

false; echo Not; echo Conditional
Your output should be similar to the following:
![Image](https://github.com/user-attachments/assets/1231c550-439d-4be1-8b47-6adf2920980b)

Note that in the previous example, all three commands still executed even though the first one failed. While you can't see from the output of the false command, it did execute. However, when commands are separated by the ; character, they are completely independent of each other.



Next, use logical "and" to separate the commands:

echo Start && echo Going && echo Gone
![Image](https://github.com/user-attachments/assets/d8defdf8-c88f-4df5-9306-8684b216a861)


Because each echo statement executes correctly, a return value of success is provided, allowing the next statement to also be executed.

Use logical "and" with a command that fails as shown below:

echo Success && false && echo Bye
![Image](https://github.com/user-attachments/assets/6713abf9-5e4a-4746-a382-fb243dd669a7)

The first echo command succeeds and we see its output. The false command executes with a failure result, so the last echo statement is not executed.

**or** command
The "or" characters separating the following commands demonstrates how the failure before the "or" statement causes the command after it to execute; however, a successful first statement causes the command to not execute:

false || echo Fail Or

![Image](https://github.com/user-attachments/assets/6e052c76-8681-429e-bb12-d2a3c7358832)
true || echo Nothing to see here
![Image](https://github.com/user-attachments/assets/413aec85-a821-48a1-9030-5a89282a1349)

