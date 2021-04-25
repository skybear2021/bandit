# Problem description: https://overthewire.org/wargames/bandit/bandit8.html
The password for the next level is stored in the file data.txt next to the word millionth

# Solution
## Step 1: Log in as bandit7.
```
─$ ssh bandit7@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit7@bandit.labs.overthewire.org's password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs 
```
## Step 2: We know that the password is next to the word millionth, so `grep` should be helpful here. 
```bash
# Syntax:
# grep "literal_string" filename
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
## Step 3: Our password should be `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`. 
