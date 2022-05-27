## Linux Command Line

## Part 1: The Command Line

What is it, how does it work and how do I get to one.

### What is it?

> A command line, or terminal, is a text based interface to the system. You are able to enter commands by typing them on the keyboard and feedback will be given to you similarly as text.

### How it's work?

> The command line typically presents you with a prompt. As you type, it will be displayed after the prompt. Most of the time you will be issuing commands

### Opening a Terminal

```
Mac    : Applications -> Utilities
Linux  :  Applications -> System  or Applications -> Utilities

Windows : intend to remotely log into another machine then you will need an SSH client. A rather good one is Putty.
```

### The Shell, Bash

> Within a terminal you have what is known as a shell. This is a part of the operating system that defines how the terminal will behave and looks after running (or executing) commands for you. There are various shells available but the most common one is called bash which stands for Bourne again shell.
>> echo: echo is a command which is used to display messages.
this will help you to know which shell you are using
<br/>
ex: echo $SHELL

### *My lovely part is Shortcuts*

> When you enter commands, they are actually stored in a history  You can traverse this history using the up and down arrow keys. So don't bother re-typing out commands you have previously entered,
you can usually just hit the up arrow a few times. You can also edit these commands using the left and right arrow keys to move the cursor where you want.

    My Notes: So this is what makes terminal easier and more fitting for programming needs from saving time and speed  

## Part 2: Basic Navigation

what do wa mean by Navigation? <br/>
basicly moving around the system <br/>
There is some commands they will help us:

* pwd : stands for Print Working Directory, It tells you what your current or present working directory.

* ls : It's short for list,It will help us to know  What's in Our Current Location?

    Paths: A path is a means to get to a particular file or directory on the system.
  * Absolute and Relative Paths: There are 2 types of paths we can use, absolute and relative. Whenever we refer to a file or directory we are using one of these paths. Whenever we refer to a file or directory, we can, in fact, use either type of path.
    * Relative path:
A file or directory location relative to where we currently are in the file system.
    * Absolute path :
A file or directory location in relation to the root of the file system.

     More on Paths: <br/>
    * ~ (tilde): - This is a shortcut for your home directory.

    * . (dot):This is a reference to your current directory.
    * .. (dotdot):This is a reference to the parent directory,  You can use this several times in a path to keep going up the hierarchy.

* cd : stands for change directory, and this work in handy way with Tab Completion (My lovely part ), If you run the command cd without any arguments then it will always take you back to your home directory.

## Part 3: More About Files

### Everything is a File

    everything is actually a file  from the text file to the keyboard one that the system reads from only.

### Linux is an Extensionless System

    Under Linux the system actually ignores the extension and looks inside the file to determine what type of file it is not like Windows system,Luckily there is a command called : file which we can use to know for certain what type of file a particular file is.

### Linux is Case Sensitive

    Linux it is possible to have two or more files and directories with the same name but letters of different case.

### Spaces in names

    Spaces in file and directory names are perfectly valid but we need to be a little careful with them, There are two ways to go:

* Quotes : using quotes around the entire item, Anything inside quotes is considered a single item.
* Escape Characters : which is a backslash ( \ ), it will escape (or nullify) the special meaning of the next character.

### Hidden Files and Directories

    If the file or directory's name begins with a . (full stop) then it is considered to be hidden.  
    You don't even need a special command or action to make a file hidden.
List the contents of a directory, including hidden files with this command:
    ls -a

## Part 4: Manual Pages

### The manual pages what are they ?

    are a set of pages that explain every command available on your system including what they do, the specifics of how you run them and what command line arguments they accept. 
    ex: man <command to look up>
    home/userBash: man ls
      -  To exit the man pages press 'q' for quit.

### Searching

    It is possible to do a keyword search on the Manual pages. This can be helpful if you're not quite sure of what command you may want to use but you know what you want to achieve.
    ex: man -k <search term>

> Note: Instead of trying to remember everything, instead remember you can easily look stuff up in the man pages.
 The man pages are your friend.

## Part 5: File Manipulation

### Making a Directory

    Linux organises it's file system in a hierarchical way.
    Creating a directory is pretty easy. The command we are after is mkdir which is short for Make Directory.
    mkdir [options] <Directory>

     -p: tells mkdir to make parent directories as needed 
     -pv: which makes mkdir tell us what it is doing

### Removing a Directory

    Creating a directory is pretty easy. Removing or deleting a directory is easy too. One thing to note, however, is that there is no undo when it comes to the command line on Linux
    ex : rmdir [options] <Directory>

### Creating a Blank File

     we can make use of this very characteristic to create blank files using the command touch.
     ex: touch [options] <filename>

### Copying a File or Directory

    we may wish to create a duplicate so that if something goes wrong we can easily revert back to the original. The command we use for this is cp which stands for copy.
    ex: cp [options] <source> <destination>

### Moving a File or Directory & Renaming Files and Directories

    To move a file we use the command mv which is short for move. It operates in a similar way to cp. One slight advantage is that we can move directories without having to provide the -r option.
    we may provide a new name for the file or directory and as part of the move it will also rename it.
    ex: mv [options] <source> <destination>

### Removing a File (and non empty Directories)

    As with rmdir, removing a file is an action that may not be undone so be careful. The command to remove or delete a file is rm which stands for remove.
    ex: rm [options] <file>

## Part 6: Cheat Sheet

    its just a  Summary for all the concepts
