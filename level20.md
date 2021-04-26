# Problem description: https://overthewire.org/wargames/bandit/bandit20.html
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

# Solution
## Step 1: Log in as bandit19
```bash
─$ ssh bandit19@bandit.labs.overthewire.org -p 2220           
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit19@bandit.labs.overthewire.org's password: IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```
## Step 2: There is an executable `bandit20-do` in current directory. We can use it run a command as another user. We can use it to read our password. 
```bash
bandit19@bandit:~$ ls
bandit20-do
bandit19@bandit:~$ file bandit20-do
bandit20-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=8e941f24b8c5cd0af67b22b724c57e1ab92a92a1, not stripped
bandit19@bandit:~$ ./bandit20-do 
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
