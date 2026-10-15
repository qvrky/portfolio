# Linux Command Line Notes

## 30/09/2026 Bandit Wargames Level 0

- First I tried to get in the game by running the command 'ssh bandit.labs.overthewire.org' and this didn't work
- I researched and learnt that, this didnt work because of a few things:

1. To access a host using SSH, you must put the username before the host name, seperated by an "@" symbol
2. To access it specifically via port 2220, you must add a flag to specify the "port" you want to use, followed by the port number itself

- Corrected command: ssh bandit0@bandit.labs.overthewire.org -p 2220 

## 30/09/2026 Bandit Wargames Level 1

- 