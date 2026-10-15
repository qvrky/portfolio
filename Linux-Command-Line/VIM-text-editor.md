# VIM text editor notes

## Fundamentals and Basic Commands

### Fundamentals
- When you run the command "vim <filename.txt>" it opens a terminal based text editor. This is VIM. It is used to edit files and code inside the terminal.

- When this page is open, you can only read the file, you cant write in it yet. To write you must clcik "i". this means "insert" and will show at the bottom of the page "Insert". You are now in write mode. To leave write mode, simply click the Esc key. you can only type VIM commands when in read mode, you can only type and edit text in write mode.

### Basic Commands

* :w - write
* :q - quit
* :q! - quit and dont save
* :wq - write and quit a.k.a save and exit
* :set number - makes the lines numbered

* dd - delete the current line selected
* you can add numbers on the back of dd to remove X amount of lines. e.g.
dd3 - removes 3 lines
dd2 - removes 2 lines

To undo something, make sure you're in command mode, and press 'u', and keep clicking it until you have removed all the mistakes, to do the opposite, lets say you undo and want to redo what you just got rid of, use 'ctrl + r' which will redo whatever you undid
searching - to search for a specific thing, like the word 'dog', type - '/' and then the thing you want to search, so '/dog'. this will highlight the word almost instantly, but when you press enter it will take your cursor to the searched word(s). Use 'n' to navigate through the searched word, for example there is 3 of the word "dog", searching with / will show you the first one, using n will go to the next, then again to the next, until there isnt anymore it will bring you back to the original one, it basically cycles through what you searched.
Lowercase n will go down or search forward, uppercase n (shift + n) will search backwards, or up.
search and replace - make sure you're in command mode and type a colon ':', then '%s' then '/' followed by the pattern or string you want to replace, then add another '/' followed by whatever it needs to be replaced with. you can only type this and it will replace the first occurance, but if you follow it with 'g' it will be 'greedy' and use c which asks for confirmation. it will ask you y/n for each one and cycle through them until youve changed each decided string to your new string replacing the old one. if you are 10000% sure you want to change each one automatically, just remove the c. c is there as a security measure to stop you from replacing things you didnt want to by asking you each time if you want to replace the string you chose, without c, it just does it automatically.

* so it would look like: :%s/dog/cat/g (automatically change each string of 'dog' to 'cat') 

**or**

* :%s/dog/cat/gc (ask for confirmation each time it tries changing 'dog' to 'cat')