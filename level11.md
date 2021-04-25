# Problem description: https://overthewire.org/wargames/bandit/bandit11.html
The password for the next level is stored in the file data.txt, which contains base64 encoded data

# Solution
## Step 1: Log in as bandit10.
```bash
$ ssh bandit10@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit10@bandit.labs.overthewire.org's password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
## Step 2: Use `base64` to decode the password. 
```bash
bandit10@bandit:~$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
