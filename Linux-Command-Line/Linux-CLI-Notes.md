# Linux Command Line Notes

## 30/09/2026 Bandit Wargames Level 0

- First I tried to get in the game by running the command 'ssh bandit.labs.overthewire.org' and this didn't work
- I researched and learnt that, this didnt work because of a few things:

1. To access a host using SSH, you must put the username before the host name, seperated by an "@" symbol
2. To access it specifically via port 2220, you must add a flag to specify the "port" you want to use, followed by the port number itself

- Corrected command: ssh bandit0@bandit.labs.overthewire.org -p 2220 

## 30/09/2026 Bandit Wargames Level 1

- 




:w means write
:q means quit
:q! means quit and dont save
:wq means write and quit so basically save and exit
dd will delete the current line selected
add numbers on the back of dd to remove X amount of lines. e.g.
dd3 - removes 3 lines
dd2 - removes 2 lines
:set number - makes the lines numbered
to undo something, make sure you're in command mode, and press 'u', and keep clicking it until you have removed all the mistakes, to do the opposite, lets say you undo and want to redo what you just got rid of, use 'ctrl + r' which will redo whatever you undid
searching - to search for a specific thing, like 'port 22', type - '/' and then the thing you want to search, so '/port 22'. this will highlight the word almost instantly, but when you press enter it will take your cursor to the searched word(s). use 'n' to navigate through the searched word, for example there is 3 port 22's, searching with / will show you the first one, using n will go to the next, then again to the next, until there isnt anymore it will bring you back to the original one, it basically cycles through what you searched. lowercase n will go down or search forward, uppercase n (shift + n) will search backwards, or up
search and replace - make sure you're in command mode and type a colon ':', then '%s' then '/' followed by the pattern or string you want to replace, then add another '/' followed by whatever it needs to be replaced with. you can only type this and it will replace the first occurance, but if you follow it with 'g' it will be 'greedy' and use c which asks for confirmation. it will ask you y/n for each one and cycle through them until youve changed each decided string to your new string replacing the old one. if you are 10000% sure you want to change each one automatically, just remove the c. c is there as a security measure to stop you from replacing things you didnt want to by asking you each time if you want to replace the string you chose, without c, it just does it automatically.       so it would look like: :%s/you/poo/g (automatically change each string of 'you' to 'poo') or :%s/you/poo/gc (ask for confirmation each time it tries changing 'you' to 'poo'

can you create a directory, create a file inside the directory, then edit that file with vim, write code in vim, in any language like HTML or Python, and then run that file as a program?


