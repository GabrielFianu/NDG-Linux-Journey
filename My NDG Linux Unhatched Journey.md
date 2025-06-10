# Basic Command Syntax

## Introduction
A command is a software program that when executed on the CLI (command line interface), performs an action on the computer. 
 
**Note:** Every part of the command is normally case-sensitive

---

### 1. Execute Command
To execute a command, type the name of the command and hit Enter. For example, in your terminal, type ls (lowercase letters) and hit Enter. 
The result should resemble the example below:

![Image](https://github.com/user-attachments/assets/e746289b-2269-4b0d-95b6-e6bc04982395)

**Try using uppercase letters**

![Image](https://github.com/user-attachments/assets/736e673d-7e99-4079-97ab-1173e417e979)

**ls command displays a listing of information about files**

---

### 2. Pattern of syntax:
command [options…] [arguments…]
You can type a command, followed by any options and/or arguments before pressing the Enter key. 
**Options** alter the behavior of the command whilst **Arguments** are items or values for the command to act upon. 

**Note:** 
Although there are some commands in Linux that aren’t entirely consistent with this syntax, most commands use this syntax or something similar.

1. Arguments
An argument can be used to specify something for the command to act upon. 

ls Documents
The resulting output is a list of files contained with the Documents directory.

![Image](https://github.com/user-attachments/assets/3ef439d1-d574-4a4a-8a5d-e0d66722ea92)

2. Options
Options can be used to alter the behavior of a command. 

ls -l

**Note:**
-l gives a long listing with relevant details

![Image](https://github.com/user-attachments/assets/8b13ad23-6968-4298-a078-47fe1706be8f)
![Image](https://github.com/user-attachments/assets/1779928e-0f8b-4dfc-82b8-03598b048843)

ls -l -r

![Image](https://github.com/user-attachments/assets/1a3c4c44-cea4-49ab-a332-e124e258fc1c)
 
ls -rl

![Image](https://github.com/user-attachments/assets/92983aa8-ca88-4bcc-8222-dfa2ea7feb27)

**Note:**
-r reverses the listing
ls -lr will give the same output

ls -r

![Image](https://github.com/user-attachments/assets/353e58e3-9f34-4587-8681-57161ae853d1)

---

### 3. Printing Working Directory
In order to discover where you are currently located within the filesystem, the pwd command can be used. 
The pwd command prints the working directory, your current location within the filesystem:

1. pwd 

The output of the above command indicates that the user is currently in their home folder, shown in the filesystem below.

![Image](https://github.com/user-attachments/assets/fdb0944c-7fc3-4f07-846e-f95c07698c49)

 ~ is equivalent to /home/sysadmin, representing the user's home directory.

---

### 4. Changing Directories
Files are used to store data such as text, graphics and programs. 
Directories are a type of file used to store other files–they provide a hierarchical organizational structure. 

Linux directory structure has a top level called root directory and it is represented by the / character.
To navigate the filesystem structure, use the **cd** (change directory) command to change directories.

cd [options] [path]
1. cd [options]

cd Documents                                               

![Image](https://github.com/user-attachments/assets/0345401a-9f40-4555-a050-048ba278dcc4)

To move to the root directory, use the / character as the argument to the cd command.

 cd /

![Image](https://github.com/user-attachments/assets/a3f4dc1c-1802-49a0-804e-8a624f1608ec)

2. cd [path]
A path is a list of directories separated by the / character. For example, /home/sysadmin is the path to your home directory:

**Absolute Paths**
An absolute path allows you to specify the exact location of a directory.  It always starts at the root directory, therefore it always begins with the / character. 
The path to the home directory /home/sysadminis an absolute path. 

cd /home/sysadmin

**No output means the command succeeded. Go ahead and confirm this using the pwd command**
pwd                                                       

![Image](https://github.com/user-attachments/assets/ae3a946a-7e40-4d0f-9780-272c7f9a99dd)

**Relative Paths**
A relative path gives directions to a file relative to your current location in the filesystem. 
Relative paths do not start with the / character, they start with the name of a directory. 

cd Documents                                               

![Image](https://github.com/user-attachments/assets/85cc05f5-8cb4-4e28-b945-42d9493a115f)

![Image](https://github.com/user-attachments/assets/ba1644ea-2a27-4fc7-bc8b-74ecb8d1b40f)

cd School/Art
Use the pwd command to confirm the change.

pwd                                      

![Image](https://github.com/user-attachments/assets/5196119b-501a-450d-89f0-7bee030bdd88)


A path can also be broken down into multiple cd commands. The following set of commands would achieve the same results:

cd School
cd Art
Shortcuts

3. The .. Characters
Regardless of which directory you are in, .. always represents one directory higher relative to the current directory, sometimes referred to as the parent directory. 
To move from the Art directory back to the School directory:

cd ..                                 

![Image](https://github.com/user-attachments/assets/c7726374-f6fc-4c6d-977a-de83b00c6b77)

4. The . Character
Regardless of which directory you are in, the . character always represents your current directory. 
For the cd this shortcut is not very useful, but it will come in handy for commands covered in subsequent sections.



5. The ~ Character
The home directory of the current user is represented by the ~ character. As stated above, you always begin as the sysadmin user, whose home is located at /home/sysadmin. 
To return to your home directory at any time execute the following command:

cd ~

![Image](https://github.com/user-attachments/assets/f72adeba-e8ae-4e00-b776-117fabc85e6f)

---

### 5. Listing Files
The ls command is used to list the contents of a directory. 

ls [OPTIONS] [FILE]
By default, when the ls command is used with no options or arguments, it will list the files in the current directory:

ls

1. ls -l
To learn the details about a file, such as the type of file, the permissions, ownerships or the timestamp, perform a long listing using the -l option to the ls command. 
Below, a listing of the /var/log directory is used as an example, since it provides a variety of output:

ls -l /var/log/

![Image](https://github.com/user-attachments/assets/e1876886-aca1-403a-a9a3-bb7101665bf4)

2. Sorting
By default the output of the ls command is sorted alphabetically by filename. It can sort by other methods as well.
The options in examples below will be combined with the -l option so the relevant details of the files are displayed. 
Notice fields corresponding to the search option.

**The -t option will sort the files by timestamp**

ls -lt /var/log                                                        

[Image](https://github.com/user-attachments/assets/6c5b97df-63ab-49b0-9ff6-2b39a9df7a66)

**The -S option will sort the files by file size**

ls -l -S /var/log                                       

![Image](https://github.com/user-attachments/assets/afc02b79-bfa3-40a6-a12d-109d9228bd53)

**The -r option will reverse the order of any type of sort. Notice the difference when it is added to the previous example**

ls -lSr /var/log

![Image](https://github.com/user-attachments/assets/0c579f61-856d-40cd-b7b6-e818470619f6)     

**The numbers in file size field switch from descending to ascending.**

**Used alone the -r option with list the files in reverse alphabetical order.**

ls -r /var/log                                            

![Image](https://github.com/user-attachments/assets/350d982a-37b6-42f6-afbc-00d85ff858a5)

---

### 6. Administrative Access
There are many Linux commands which deal with sensitive information like passwords, system hardware, or otherwise operate under other exceptional circumstances. 
Preventing regular users from executing these commands helps to protect the system.  Logging in as the root user provides administrative access, allowing for the execution of some of the privileged commands.

1. The su Command
su OPTIONS USERNAME
The su command allows you to temporarily act as a different user. 
By default, if a user account is not specified, the su command will open a new shell as the root user, which provides administrative privileges.

Utilizing the login shell option is recommended, as the login shell fully configures the new shell with the settings of the new user. 
This option can be specified one of three ways:

su -
su -l
su --login 
After executing the su command, a password is required. 

**Note:**
As a security measure, the password will not be visible as it is typed.

su -
Password:


![Image](https://github.com/user-attachments/assets/e56cca3f-1d21-4a36-ad94-20e0d834a2a8)

**Note**: 
the command prompt has changed to reflect that you are now logged in as the root user. 

2. The sudo Command
sudo [OPTIONS] COMMAND
The sudo command allows a user to execute a command as another user without creating a new shell. 
Instead, to execute a command with administrative privileges, use it as an argument to the sudo command. 
The sudo command can be used to switch to other user accounts as well. To specify a different user account use the -u option.

Execute the sl command as the root user by putting sudo in front of it:
**The prompt for the password will not appear again as long as the user continues to execute sudo commands less than five minutes apart.**

sudo sl
[sudo] password for sysadmin:

![Image](https://github.com/user-attachments/assets/9808ba48-abaa-409d-ac59-39eff656b775)

---

### 7. Permissions
Permissions determine the ways different users can interact with a file or directory. 
When listing a file with the ls -l command, the output includes permission information. 
For the example we will use a script called hello.sh located in the Documents directory:

Use the following command to switch to the Documents directory:

cd ~/Documents
ls -l hello.sh                                   

![Image](https://github.com/user-attachments/assets/0d6900c1-10a7-4e78-a5ec-982f994a947d)

Below is a review of the fields relevant to permissions.

File Type Field
-rw-r--r-- 1 sysadmin sysadmin 647 Dec 20  2017 hello.sh
The first character of this output indicates the type of a file. If the first character is a -, this is a regular file. If the character was a d, it would be a directory.
After the file type character, the permissions are displayed. There are three different permissions that can be placed on a file or directory: read (r), write (w), and execute (x).

1. Changing File Permissions
The chmod command is used to change the permissions of a file or directory. 
Only the root user or the user who owns the file is able to change the permissions of a file.

chmod [<SET><ACTION><PERMISSIONS>]... FILE

ls -l hello.sh                                     

![Image](https://github.com/user-attachments/assets/f9335851-cc15-4718-bde5-4eb1f2c704d5)

Currently, the execute permission is not set for any of the permission groups and attempting to execute this script using the following syntax fails.

./hello.sh                                       

![Image](https://github.com/user-attachments/assets/bb40bb11-3650-485b-82b1-f37ab677f488)

chmod u+x hello.sh

![Image](https://github.com/user-attachments/assets/785cef2a-e056-45ff-8adb-9bcc5ffd00de)

No output indicates the command succeeded. Confirm by checking the permissions using the ls -l command.

ls -l hello.sh                                     
The user owner now has the execute permission listed.

![Image](https://github.com/user-attachments/assets/56083f4f-f329-41bb-9054-15e3dfb1a067)

Execute hello.sh: 
./hello.sh                                     

![Image](https://github.com/user-attachments/assets/ba1fd5f2-c841-4624-9ee2-c21eee67626a) 

**Notice**
To execute the script in the previous example, a ./ character combination was placed before the script name.

This indicates the "command" should be run from the current directory.


2. Changing File Ownership
Initially, the owner of a file is the user who creates it. The chown command is used to change the ownership of files and directories. 
Changing the user owner requires administrative access. A regular user cannot use this command to change the user owner of a file, even to give the ownership of one of their own files to another user. 

To change the user owner of a file, the following syntax can be used: 

chown [OPTIONS] [OWNER] FILE 

ls -l                                           

To switch the owner of the hello.sh script to the root user, use root as the first argument and hello.sh as the second argument. 
Don't forget to use the sudo command in order to gain the necessary administrative privileges. 

sudo chown root hello.sh                        
Confirm the user owner has changed by executing the ls -l command. Use the filename as an argument to limit the output:

ls -l hello.sh                                  
-rwxr--r-- 1 root sysadmin 647 Dec 20  2017 hello.sh  
The user owner field is now root indicating the change was successful.

![Image](https://github.com/user-attachments/assets/b338ffef-d646-4d2e-b223-f265d8094772)

Try executing the hello.sh script again. 

./hello.sh                                        

![Image](https://github.com/user-attachments/assets/ce1d70e5-a696-4527-a1d0-a48718e192ad)

It fails! Why?
Only the user owner has the execute permission, and now the root user is the user owner. 
This file now requires administrative access to execute. Use the sudo command to execute the script as the root user.

sudo ./hello.sh                                 

![Image](https://github.com/user-attachments/assets/1eb1eb3e-f734-4898-85a5-5cf3d990a8ee)

---

### 8. Viewing Files
There are a few Linux commands available to view the content of files. 
The cat command, which stands for “concatenate”, is often used to quickly view the contents of small files.

1. The cat command will display the entire contents of the file, hence why it is mainly recommended for smaller files where the output is limited and does not require scrolling. 

cat [OPTIONS] [FILE]

cd ~/Documents
cat animals.txt                            

![Image](https://github.com/user-attachments/assets/4a78cc23-b1ec-4397-b3b6-42b6ec60f484)

The cat command displays all five lines of the file above. When viewing larger files, the cat command can result in very lengthy output that cannot be paused to scroll through. 
A better method of viewing long text files, is with a pager command which has a functionality that can pause and scroll through the output of the file.

2. Head and Tail Method
Another way to view the content of files is by using the head and tail commands. These commands are used to view a select number of lines from the top or bottom of a file. 

head [OPTIONS] [FILE]
tail [OPTIONS] [FILE]

cat alpha.txt       

![Image](https://github.com/user-attachments/assets/e36ba0e7-733b-44c8-90b6-3a3b855c4fb9)

In the example above, all twenty-six lines of the file are displayed. To filter the output and view lines from the top of the alpha.txt file, use the head command:

head alpha.txt                          

![Image](https://github.com/user-attachments/assets/3b49af21-392a-4e4b-8126-5c2d5f610f5e)

Then, to view lines at the bottom of the alpha.txt file, you use the tail command:

tail alpha.txt                          

![Image](https://github.com/user-attachments/assets/80fc6c11-e99d-4f1c-b317-5a657e963073)

By examining the output of the head and tail commands above, you can see that the default behavior of the head and tail commands in this shell is to display ten lines.

3. The -n option with the head and tail commands can be used to specify the amount of lines to display. To use the -n option, specify the amount of lines from the file you want to display after the option and use the filename as an argument:

head -n number of lines filename
For example, to change the output of the head command to view the first five lines of the alpha.txt file:

head -n 5 alpha.txt                    

![Image](https://github.com/user-attachments/assets/79a792d8-1c4b-4b23-9f84-fd909014c304)

View the last five lines of the alpha.txt file:

tail -n 5 alpha.txt 

![Image](https://github.com/user-attachments/assets/62a4d8f3-6bdf-4581-9955-06d644f27229)

---

### 9. Copying Files
The cp command is used to copy files.

cp [OPTIONS] SOURCE DESTINATION

cp /etc/passwd .

![Image](https://github.com/user-attachments/assets/e3b6a961-3a27-441d-abdf-85cf6c78a4ad)


Note
The second argument is the . character. 

ls

![Image](https://github.com/user-attachments/assets/fcc0da1e-48da-4519-8211-884672a92f91)


Permissions can have an impact on file management commands, such as the cp command. In order to copy a file, it is necessary to have execute permission to access the directory where the file is located and the read permission for the file being copied.
It is also necessary to have write and execute permission on the directory the file is being copied to. Typically, there are two places where you should always have write and execute permission on the directory: your home directory and the /tmp directory.

---

### 10. Moving Files
The mv command is used to move a file from one location in the filesystem to another.

mv SOURCE DESTINATION
The mv command requires at least two arguments. The first argument is the source, a path to the file to be moved. The second argument is the destination, a path to where the file will be moved to. 
The files to be moved are sometimes referred to as the source, and the place where the files are to be placed is called the destination.

 cd ~/Documents
1. To move the people.csv file into the Work directory, use the filename as the source, and the directory name as the destination:

 mv people.csv Work                              
If a file is moved from one directory to another without specifying a new name for the file, it will retain its original name. 

![Image](https://github.com/user-attachments/assets/043fc415-b1e1-4673-a857-8567c0e119d4)

ls Work                                         
people.csv

![Image](https://github.com/user-attachments/assets/c845ab07-e77c-44cb-89a0-8b8ed6efcfd3)

2. The mv command is able to move multiple files, as long as the final argument provided to the command is the destination. For example, to move three files into the School directory:

mv numbers.txt letters.txt alpha.txt School  

![Image](https://github.com/user-attachments/assets/c023e2e0-0924-41f8-b560-57387528f6f9)
      
ls School                                         

![Image](https://github.com/user-attachments/assets/09cbd9cf-6bc7-4eb2-ba2a-1c29c34e6750)

3. Moving a file within the same directory is an effective way to rename it. For example, in the following example the animals.txt file is given a new name of zoo.txt:

mv animals.txt zoo.txt

ls                                              

![Image](https://github.com/user-attachments/assets/34205f40-49b2-4ed1-a82d-77acefb2ff4e)

mv animals.txt zoo.txt  

![Image](https://github.com/user-attachments/assets/78b02bde-5cdd-4ac1-bebb-f8e50d509ffd)
                        
ls                                                

![Image](https://github.com/user-attachments/assets/29979d05-b92f-4084-8d14-583bd5157331)


**Permissions can have an impact on file management commands, such as the mv command. Moving a file requires write and execute permissions on both the origin and destination directories.**

---

### 11. Removing Files
The rm command is used to delete files and directories. It is important to keep in mind that deleted files and directories do not go into a "trash can" as with desktop-oriented operating systems. 
**When a file is deleted with the rm command, it is almost always permanently gone.**

rm [OPTIONS] FILE

cd ~/Documents

1. Without any options, the rm command is typically used to remove regular files:

rm linux.txt

![Image](https://github.com/user-attachments/assets/73a752c2-26f9-4917-b856-0c7579b142e7)

ls linux.txt
ls: cannot access linux.txt: No such file or directory 

2. The rm command will ignore directories that it's asked to remove; to delete a directory, use a recursive option, either the -r or -R options. 
**Just be careful since these options are "recursive", this will delete all files and all subdirectories**

rm Work
rm: cannot remove 'Work': Is a directory

![Image](https://github.com/user-attachments/assets/6f8af517-1d25-46d8-8afd-228f7cf3ba95)

rm -r Work

![Image](https://github.com/user-attachments/assets/38071020-ccfb-483a-89cc-24f5685e4f47)

ls Work                                         
ls: cannot access Work: No such file or directory

![Image](https://github.com/user-attachments/assets/38071020-ccfb-483a-89cc-24f5685e4f47)

**Warning**
The rm command removes files permanently. To repeat the examples above, reset the terminal using the reset button.

**Note:**
Permissions can have an impact on file management commands, such as the rm command.
To delete a file within a directory, a user must have write and execute permission on a directory. Regular users typically only have this type of permission in their home directory and its subdirectories.

---

### 12. Filtering Input
The grep command is a text filter that will search input and return lines which contain a match to a given pattern.

grep [OPTIONS] PATTERN [FILE]

grep sysadmin passwd                               
sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash 


The command above returned the line from the passwd which contains the pattern sysadmin.


**Regular Expressions**
Regular expressions have two common forms: basic and extended. Most commands that use regular expressions can interpret basic regular expressions. 
However, extended regular expressions are not available for all commands and a command option is typically required for them to work correctly.

The following summarizes basic regular expression characters:

Basic Regex Character(s)	Meaning
.	Any one single character
[ ]	Any one specified character
[^ ]	Not the one specified character
*	Zero or more of the previous character
^	If first character in the pattern, then pattern must be at beginning of the line to match, otherwise just a literal ^
$	If last character in the pattern, then pattern must be at the end of the line to match, otherwise just a literal $
The following table summarizes the extended regular expressions, which must be used with either the egrep command or the -E option with the grep command:

Extended Regex Character(s)	Meaning
+	One or more of the previous pattern
?	The preceding pattern is optional
{ }	Specify minimum, maximum or exact matches of the previous pattern
|	Alternation - a logical "or"
( )	Used to create groups
Only basic regular expressions have been covered here. For more information concerning extended regular expressions, check out the NDG Linux Essentials and NDG Introduction to Linux courses.

Basic Patterns
Regular expressions are patterns that only certain commands are able to interpret. Regular expressions can be expanded to match certain sequences of characters in text. The examples displayed on this page will make use of regular expressions to demonstrate their power when used with the grep command. In addition, these examples provide a very visual demonstration of how regular expressions work, the text that matches will be displayed in a red color.

grep sysadmin passwd                               
sysadmin:x:1001:1001:System Administrator,,,,:/home/sysadmin:/bin/bash

grep 'root' passwd
root:x:0:0:root:/root:/bin/bash                                                 
operator:x:1000:37::/root:

![Image](https://github.com/user-attachments/assets/9929df3b-d281-44d7-a872-b0d395372eb7)

To prevent the shell from misinterpreting them as special shell characters, these patterns should be protected by strong quotes, which simply means placing them between single quotes.

1. The first anchor character ^ is used to ensure that a pattern appears at the beginning of the line. 
For example, to find all lines in /etc/passwd that start with root use the pattern ^root. Note that ^ must be the first character in the pattern to be effective.

grep '^root' /etc/passwd

![Image](https://github.com/user-attachments/assets/4a3a575f-0100-49d8-9322-31b4f39cda00)

For the next example, first examine the alpha-first.txt file. The cat command can be used to print the contents of a file:
cat alpha-first.txt                             

![Image](https://github.com/user-attachments/assets/f94a83cc-2941-4a8d-a8ed-be17b8bad9c4)

2. The second anchor character $ can be used to ensure a pattern appears at the end of the line, thereby effectively reducing the search results. 
To find the lines that end with an r in the alpha-first.txt file, use the pattern r$:

grep 'r$' alpha-first.txt

![Image](https://github.com/user-attachments/assets/12fa8bd4-3a89-4d8f-a112-4e13c178e642)

Again, the position of this character is important, the $ must be the last character in the pattern in order to be effective as an anchor.

3. Match a Single Character With .
The following examples will use the red.txt file:

cat red.txt

![Image](https://github.com/user-attachments/assets/f1db5daf-d865-41bd-84ac-da6f76e76ae7)

One of the most useful expressions is the period . character. It will match any character except for the new line character. 
The pattern r..f would find any line that contained the letter r followed by exactly two characters (which can be any character except a newline) and then the letter f:

grep 'r..f' red.txt
reef
roof

The same concept can be repeated using other combinations. The following will find four letter words that start with r and with d:

grep 'r..d' red.txt
reed
read

![Image](https://github.com/user-attachments/assets/3124186e-3393-417b-9add-0bbefd75e558)

This character can be used any number of times. To find all words that have at least four characters the following pattern can be used:

grep '....' red.txt                             

![Image](https://github.com/user-attachments/assets/16c4ef74-8d82-47cf-a0a0-e78f9844baca)

The line does not have to be an exact match, it simply must contain the pattern, as seen here when r..t is searched for in the /etc/passwd file:

grep 'r..t' /etc/passwd

![Image](https://github.com/user-attachments/assets/97718c14-f014-4133-8dbe-c97627ec4965)

4. Match a Single Character With []
The square brackets [ ] match a single character from the list or range of possible characters contained within the brackets.
For example, given the profile.txt file:

cat profile.txt

![Image](https://github.com/user-attachments/assets/e26ab91d-2a67-4811-9b29-ab0f85787f41)

To find all the lines in the profile.txt which have a number in them, use the pattern [0123456789] or [0-9]:

grep '[0-9]' profile.txt

![Image](https://github.com/user-attachments/assets/811d9ce2-2cb2-431d-8b1b-435553a80af4)

On the other hand, to find all the lines which contain any non-numeric characters, insert a ^ as the first character inside the brackets. This character negates the characters listed:

grep '[^0-9]' profile.txt

![Image](https://github.com/user-attachments/assets/bf07fb47-b540-452d-899c-4e2a339ecb8d)

**Note**

Do not mistake [^0-9] to match lines which do not contain numbers. 
It actually matches lines which contain non-numbers. Look at the original file to see the difference. 
The third and sixth lines only contain numbers, they do not contain non-numbers so those lines do not match.

When other regular expression characters are placed inside of square brackets, they are treated as literal characters. For example, the . normally matches any one character, but placed inside the square brackets, then it will just match itself. In the next example, only lines which contain the . character are matched.

grep '[.]' profile.txt

![Image](https://github.com/user-attachments/assets/d698e9c2-8a70-472f-8322-b8e146585e82)

4. Match a Repeated Character Or Patterns With *
The regular expression character * is used to match zero or more occurrences of a character or pattern preceding it. For example e* would match zero or more occurrences of the letter e:

cat red.txt

![Image](https://github.com/user-attachments/assets/6b5f3e80-5863-45d1-a458-42a999b1a22c)

grep 're*d' red.txt

![Image](https://github.com/user-attachments/assets/da79911f-4337-4728-92b6-b24dbb0e5eaa)

It is also possible to match zero or more occurrences of a list of characters by utilizing the square brackets. The pattern [oe]* used in the following example will match zero or more occurrences of the o character or the e character:

grep 'r[oe]*d' red.txt

![Image](https://github.com/user-attachments/assets/d4e8815f-c087-45c1-b673-b5ef7dbf6d50)

When used with only one other character, * isn't very helpful. Any of the following patterns would match every string or line in the file: .* e* b* z*.

grep 'z*' red.txt

![Image](https://github.com/user-attachments/assets/5fec4dff-296c-4827-aa5a-43bf8b889237)

grep 'e*' red.txt

![Image](https://github.com/user-attachments/assets/fca8c0bb-d81c-4cee-bcda-dd9093e1a6d7)

This is because * can match zero occurrences of a pattern. In order to make the * useful, it is necessary to create a pattern which includes more than just the one character preceding *. For example, the results above can be refined by adding another e to make the pattern ee* effectively matching every line which contains at least one e.

grep 'ee*' red.txt

Standard Input

![Image](https://github.com/user-attachments/assets/4dc19e62-a236-4cec-b5f0-ccf3151dac39)

If a file name is not given, the grep command will read from standard input, which normally comes from the keyboard with input provided by the user who runs the command. This provides an interactive experience with grep where the user types in the input and grep filters as it goes. Feel free to try it out, just press Ctrl-D when you're ready to return to the prompt.

---


### 13. Shutting Down
The shutdown command arranges for the system to be brought down in a safe way. 
All logged-in users are notified that the system is going down and within the last five minutes leading up to the shutdown, new logins are prevented.

shutdown [OPTIONS] TIME [MESSAGE]

The shutdown command requires administrative access, switch to the root account for this section using the following command. 

su -                                                   

![Image](https://github.com/user-attachments/assets/1b9283fb-f9ce-4dff-b806-5f29dbc06a9b)

shutdown now                                         
                                                                                
Broadcast message from sysadmin@localhost                                       
        (/dev/pts/0) at 2:05 ...                                              
                                                                                
The system is going down for maintenance NOW! 

Unlike other commands used to bring the system down, the shutdown command requires a time argument specifying when the shutdown should begin. Formats of this time argument can be the word now, a time of day in the format hh:mm or the number of minutes to delay in the format +minutes.

shutdown 01:51                                                
                                                                               
![Image](https://github.com/user-attachments/assets/bcaa5779-e3df-4feb-8dbd-e317ed28b42d)

The shutdown command also has an optional message argument, indicating a message that will appear in the terminals of all users. For example:

shutdown +1 "Goodbye World!"                                  
                                                                                                                                               
![Image](https://github.com/user-attachments/assets/42b8760a-7b3c-4498-8977-911560197a36)

--

### 14. Network Configuration
1. The ifconfig command stands for "interface configuration" and is used to display network configuration information.

ifconfig [OPTIONS] 

ifconfig                                     

![Image](https://github.com/user-attachments/assets/ab5d565a-690d-4267-ab82-19f3f75c816a)

2. The ping command is used to verify connectivity between two computers. It does this by sending packets to another machine on a network. If the sender receives a response it should be possible to connect to that machine.
Information is sent using “packets”; the encapsulated unit of data sent over a network. In order for the packets to find the other computer, they will need an address. The ping command uses IP addresses to identify a computer on the network that it wants to connect to.
By default, the ping command will continue sending packets until the break command (CTL + C) is entered at the console. To limit how many pings are sent, use the -c option followed by the number of pings to be sent. The example below shows ping being limited to 4 iterations with -c 4.

If the ping command is successful, you will see output like the following:

ping -c 4 192.168.1.2                                       

![Image](https://github.com/user-attachments/assets/8fbb220c-8412-42d5-8b21-c74155c8b936)

**If the ping command fails, you will receive a message stating, Destination Host Unreachable**

The ping command may fail even though the remote machine is connecting. This is because some administrators configure their machines, or even entire networks, not to respond to ping requests as a security measure.
The ping command also works with a hostname, or domain name like yahoo.com. Using this first saves time, if that ping command is successful, there is proper name resolution AND the IP address is functioning properly as well.

---

### 14. Viewing Processes
Running a command results in something called a process. In the Linux operating system, processes are executed with the privileges of the user who executes the command. This allows for processes to be limited to certain capabilities based upon the user identity.
Although there are exceptions, generally the operating system will differentiate users based upon whether they are the administrator. Typically regular users, like the sysadmin user, cannot control another user's processes. 
Users who have administrative privileges, like the root account, can control any user processes, including stopping any user process.

The ps command can be used to list processes.

ps [OPTIONS]

1. ps
ps

![Image](https://github.com/user-attachments/assets/bf5f8c8b-0d3f-47c5-b6fd-ef77b1aa27f5)

The ps command will display the processes that are running in the current terminal by default. 
PID: The process identifier, which is unique to the process. This information is useful for controlling the process by its ID number.

TTY: The name of the terminal where the process is running. This information is useful for distinguishing between different processes that have the same name.

TIME: The total amount of processor time used by the process. Typically, this information isn't used by regular users.

CMD: The command that started the process.

2. Instead of viewing just the processes running in the current terminal, users may want to view every process running on the system. The -e option will display every process:

ps -e

![Image](https://github.com/user-attachments/assets/a7fe300e-0e5e-434f-8323-cffc425a89f7)

3. Typically, the -f option is also used as it provides more detail in the output of the command, including options and arguments. Look for the ps command on the last line, the CMD column now includes the options used:

ps -ef

![Image](https://github.com/user-attachments/assets/e3d2452b-37bb-477a-bbcd-475e1306f209)

---

### 15. Installing Packages
Package files are commonly installed by downloading them directly from repositories located on Internet servers. 
The Debian repositories contain more than 65,000 different packages of software. Before installing a package, it is good practice to refresh the list of available packages using the apt-get update command.

Please allow a few minutes for the following commands to execute.
sudo apt-get update

![Image](https://github.com/user-attachments/assets/99e4a375-a016-451e-88fd-db10fc77af7d)

1. To search for keywords within these packages, you can use the apt-cache search command.

apt-cache search [keyword]
The keyword that is used should match part of the name or description of the package that is to be located. Multiple keywords can be used to further clarify the search; for example, the search term web server would provide better results than web or server.

To find packages associated with the cow keyword:

apt-cache search cow                                      

![Image](https://github.com/user-attachments/assets/b97edfec-d0bf-49b4-9a66-c06c60862227)

sudo apt-get install [package]
sudo apt-get install cowsay                               

![Image](https://github.com/user-attachments/assets/9c2921a1-7866-489d-bd20-0f60326046c5)

The cowsay command is a configurable talking cow! Use a word or phrase as an argument:

cowsay 'NDG Linux Unhatched'                              
 
![Image](https://github.com/user-attachments/assets/f9fa48b6-6c70-4cff-b79c-b5b55376c215)

**We recommend enclosing the argument in single quotes to prevent the shell from interpreting special characters.**

2. Updating Packages
The apt-get install command can also update a package, if that package is installed and a newer version is available. 
If the package is not already on the system, it would be installed; if it is on the system, it would be updated.

Updating all packages of the system should be done in two steps. First, update the cache of all packages available with apt-get update.
Second, execute the apt-get upgrade command and all packages and dependencies will be updated.

apt-get update
apt-get upgrade

sudo apt-get update                                           

![Image](https://github.com/user-attachments/assets/40ae091f-660c-42ea-8f38-c9f3cdadf7d1)                                              

sudo apt-get upgrade                                      

![Image](https://github.com/user-attachments/assets/b95fe56f-76ca-42d0-91e9-17eeed994e20)

3. Removing Packages
The apt-get command is able to either remove or purge a package. The difference between the two is that purging deletes all package files, while removing deletes all but the configuration files for the package.
An administrator can execute the apt-get remove command to remove a package or the apt-get purge command to purge a package completely from the system.

apt-get remove [package]
apt-get purge [package]
For example, to purge cowsay completely, execute the following command. Enter Y when prompted:

sudo apt-get purge cowsay                                 

![Image](https://github.com/user-attachments/assets/5f0c9b42-8f34-4e24-b56e-476448121345)

---

### 15. Updating User Passwords
The passwd command is used to update a user’s password. Users can only change their own passwords, whereas the root user can update the password for any user.

passwd [OPTIONS] [USER]
For example, since we are logged in as the sysadmin user we can change the password for that account. Execute the passwd command. You will be prompted to enter the existing password once and the new password twice. 
For security reasons, no output is displayed while the password is being typed. The output is shown as follows:

sysadmin@localhost:~$ passwd                                                    

![Image](https://github.com/user-attachments/assets/566202a3-35cc-4733-990d-176aa4cf281c)

If the user wants to view status information about their password, they can use the -S option:

sysadmin@localhost:~$ passwd -S sysadmin                                        

![Image](https://github.com/user-attachments/assets/8bc98cb8-3cc4-4a5e-84ea-075ac6a22b51)


su root                                                   

** Change of Password**
The root user can change the password of any user. If the root user wants to change the password for sysadmin, they would execute the following command:

passwd sysadmin                                               

![Image](https://github.com/user-attachments/assets/3c4f08cd-8836-4288-a78e-8bf4931a5066)

**Exit the root account** using the exit command:

root@localhost:~# exit                                                        
exit   

![Image](https://github.com/user-attachments/assets/fa8a4830-d0f3-45ea-a9b6-3b3bf3b59381)

---

### 16. Redirection
Adding content to files in Linux can be done in a variety of ways. Linux has a few text editors that can be used to add content to a file.
However, this method requires some familiarity with Linux text editor commands.

When it comes to command input and output there are three paths, or “tracks”. These paths are called file descriptors. 
The first file descriptor is standard input, abbreviated as STDIN. Standard input is the information the command receives and processes when it is executed, essentially what a user types on the keyboard. 
The second file descriptor is standard output, abbreviated as STDOUT. Standard output is the information that the command displays, the output of the command. 
The last file descriptor is standard error, abbreviated as STDERR. STDERR, are the error messages generated by commands that are not correctly executed. The following are examples of how file descriptors will appear in the terminal:

1. Standard Input (STDIN)
sysadmin@localhost:~$ ls ~/Documents

2. Standard Output (STDOUT)
sysadmin@localhost:~$ ls                                                        
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos

3. Standard Error (STDERR)
sysadmin@localhost:~$ ls fakefile                                               
ls: cannot access fakefile: No such file or directory

This section will cover one of the three file descriptors, STDOUT, and how to redirect STDOUT from where you normally see it, in the terminal, to a file in the filesystem. 
To use redirection, simply use a greater-than symbol > along with a filename:

[COMMAND] > [FILE]

To demonstrate redirection, we will use the output of the cat command. Without redirection, the output of the cat command will be displayed in the terminal:

sysadmin@localhost:~$ cd ~/Documents
sysadmin@localhost:~/Documents$ cat food.txt                                    
Food is good.

![Image](https://github.com/user-attachments/assets/56f0c05a-cdbb-4831-adc0-bb8c0e0fda8a)

Now use the > character to redirect the STDOUT of the cat food.txt command above to a new file called newfile1.txt:

cat food.txt > newfile1.txt
sysadmin@localhost:~/Documents$

![Image](https://github.com/user-attachments/assets/29b91418-0b4d-43cf-ae2c-6104685b86e3)

As you can see, there is no output displayed since the STDOUT has been redirected to the newfile1.txt file. Verify that the STDOUT of the cat food.txt command is in newfile1.txt:

cat newfile1.txt                     
Food is good.

![Image](https://github.com/user-attachments/assets/29b91418-0b4d-43cf-ae2c-6104685b86e3)

This is useful if you need to copy content from an important file to another file in order to edit the contents without modifying the original file. 
However, what if you want to add a comment or note to a file? To do this, you can use the echo command. The echo command is used to print output in the terminal:

echo "Hello"           
Hello                                                                   

![Image](https://github.com/user-attachments/assets/ee9caab8-c63e-49cb-a526-ee887f4ff4be)

Printing comments to the screen is a fun feature but the echo command can be made more useful by using redirection. 
Using the echo command, content can be added to the newfile1.txt file:

cat newfile1.txt         
Food is good.     

echo "I like food." > newfile1.txt
cat newfile1.txt             
I like food.                                           

![Image](https://github.com/user-attachments/assets/3d716bf0-ac63-4cf8-b08f-49a14e122933)


Notice that the STDOUT of the echo command has replaced the original content of the file. This is because the single > character will overwrite any contents in an existing file. 
To append rather than overwrite content to a file, use a double greater-than symbol >>:

echo "This food is good." >> newfile1.txt
cat newfile1.txt              

![Image](https://github.com/user-attachments/assets/169004a7-5caa-43fe-ad03-d02002023ad3)

**To redirect information to an existing file, the user must have write permissions on that file.**

---


