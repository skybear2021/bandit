# Problem description: https://overthewire.org/wargames/bandit/bandit10.html
The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

# Solution
## Step 1: Log in as bandit9.
```bash
└─$ ssh bandit9@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit9@bandit.labs.overthewire.org's password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
## Step 2: We can use `strings` to print out printable strings from `data.txt`. Then we can use grep to filter out the lines containing `=`. 
```bash
bandit9@bandit:~$ strings data.txt | grep =
========== the*2i"4
=:G e
========== password
<I=zsGi
Z)========== is
A=|t&E
Zdb=
c^ LAh=3G
*SF=s
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
S=A.H&^
```
## Step 3: It looks like that `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk` is the password.
