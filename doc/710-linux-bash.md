

# Using linux, bash, commands, ...

What does the command line do?
It lets us launch and interact with "processes".

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


