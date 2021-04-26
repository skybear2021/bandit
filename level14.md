# Problem description: https://overthewire.org/wargames/bandit/bandit14.html
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14.

# Solution
## Step 1: Log in as bandit13
```bash
ssh bandit13@bandit.labs.overthewire.org -p 2220
bandit13@bandit.labs.overthewire.org's password: 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
## Step 2: There is a private key in current directory. We can use it to log in as bandit14.
```bash
ssh bandit14@localhost -i sshkey.private
```
## Step 3: Since we are in as bandit14, let's read `/etc/bandit_pass/bandit14` file. 
```bash
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```
