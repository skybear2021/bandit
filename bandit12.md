# Problem description: https://overthewire.org/wargames/bandit/bandit12.html
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

# Solution
## Step 1: Log in as bandit11. 
```bash
─$ ssh bandit11@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit11@bandit.labs.overthewire.org's password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
## Step 2: We know that the letters in the password have been rotated by 13 positions, i.e. `a` actually means `n`. In this case, we can use `tr` help us do the translation. 
```bash
bandit11@bandit:~$ cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
