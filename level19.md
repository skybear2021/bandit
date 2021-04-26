# Problem description: https://overthewire.org/wargames/bandit/bandit19.html
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
# Solution
## Step 1: Log in as bandit18
```bash
└─$ ssh bandit18@bandit.labs.overthewire.org -p 2220                                                                                                                    1 ⨯
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```
## Step 2: We get `Bye` message in step 1. It looks like we cannot log in with SSH. Since we know that the password is in file `/home/bandit18/readme`, we can use SSH to read the file content. 
```bash
─$ ssh bandit18@bandit.labs.overthewire.org -p 2220 "cat /home/bandit18/readme"
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit18@bandit.labs.overthewire.org's password: 
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```
