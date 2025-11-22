

# Using linux, bash, commands, ...

What does the command line do?
It lets us launch and interact with "processes".
A process?
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


