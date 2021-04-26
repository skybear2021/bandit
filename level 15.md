# Problem description: https://overthewire.org/wargames/bandit/bandit15.html
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

# Solution
## Step 1: Log in as bandit14
```bash
─$ ssh bandit14@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit14@bandit.labs.overthewire.org's password: 
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```
## Step 2: Send current password `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e` to port 30000 on localhost. We can use `nc` command. 
```bash
bandit14@bandit:~$ echo "4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e" | nc localhost 30000
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
```
