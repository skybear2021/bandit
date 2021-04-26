# Problem description: https://overthewire.org/wargames/bandit/bandit18.html
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

# Solution
## Step 1: Log in as bandit17. 
Refer https://github.com/skybear2021/bandit/blob/main/level17.md
## Step 2: Do a diff between file `passwords.new`  and `passwords.old`. 
```bash
bandit17@bandit:~$ diff passwords.new passwords.old 
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
```
`kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` is from file `passwords.new`, and it is the password we are looking for. 
