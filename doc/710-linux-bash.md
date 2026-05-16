
# Using linux, bash, commands, ...

What does the terminal do?
It lets us launch and interact with "processes".

## First steps at the command prompt

We will begin by entering single commands, where we type a program name.

**TODO** the following is not as useful as I thought, but reworked?

It may be simpler to change to the directory where the offending file is. Do you know this trick: 
* First run ```cd``` - it should Change Directory for you, and take you to your "home" directory, which is  /home/qubes for you.
* Run ```pwd``` to see where you are. ```ls``` shows that QubesIncoming is here.
* Now type ```cd Q\<tab key>``` where \<tab key> means to press that key on the keyboard (it might look like this:  <big>↹ </big>).
    * If there is only one item beginning with 'Q' in the directory, then it will be filled in magically, and you can press the \<return> key.
    * If there are other items beginning with Q, then the name will be filled as much as possible. You can type some extra to choose which one.
    * If you press \<return> and there is "Not found" or other error, use the up arrow key to get the last command back, ready for you to change it.

Now you have less to type when there are long filenames. You are already in /home/qubes/QubesIncoming/ directory.

If you want visual method, type ```thunar``` - if a window appears, select the menu "View>Show hidden items". There is surely a way to delete the folder permanently, but I do not know it :frowning: 

To continue in the terminal:

* Enter and run  ```ls -a``` to see the hidden directory name.
* If you want to move a directory to another qube,  
  ```qvm-move-to-vm destinationqube .\<tab>```
   will fill in the name of the directory.
* If you want to delete it, then you can use
   ```rm -r .backup#restore``` , or ```rm -rf ...``` if there are read-only problems.



## About processes

What is a process?
* computes - it is normally launched from a file containing instructions
* can read and write to files
* can interact with many other parts of the system 
Some key points about processes:
* can run in a "shell"
* ...in "foreground", where the process sees what you type
* ...in background, where it doesn't
* ...or be completely independent
* can be stopped and restarted
* can be killed

To make a process, we will need a "shell". Our shell needs a "terminal".

aside: history of terminals... todo.
A terminal combines a keyboard and a display. Normally, there is a process listening to what you type, and maybe outputting text or other data to the display.

Try: open a terminal, don't type anything yet.

your terminal is providing a keyboard and a display to your first process: a shell.
The shell:
* It's probably a "bash" shell. There are other types.
*  it knows it is running in a terminal, so:
    *   it has probably displayed a message
    *  it has displayed a "prompt" - it want you to type a command.

will use echo - ignores input, but outputs what you tell it to.

--> arguments
echo argument1 argument2
first real cmdline.
use up arrow, add more spaces between arguments - no change to the output. bash splits up the commad line to make a list of arguments, given to the echo process.

to make an argument with spaces, use single quotes ' (not the same as ` or ")

pwd. - part of environment for a process

todo: filesystem, files and directories.

## Using bash history

(todo : fix markdown)
repeat last command: ```!!```

use recent: up and down arrow keys. Can edit it. Press return to run it.

view history:
    ```history``` to see all history
    ```history 10``` to see the last 10
Use the numbers to rerun: !102

modifiers, can be used after a \::
    :p   print it and make it the last item in history 

    
    


delete an item :
    ```history -d <number>``` then ```history -w```


## Commands in Dom0

### Copy or move files from Dom0 to another qube

The first parameter of ```qvm-move-to-vm``` is the name of the destination qube. After that, the paths of the files/directories you want to move. 

Make sure the destination has enough free space.


