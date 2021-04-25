# Problem description: https://overthewire.org/wargames/bandit/bandit9.html
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

# Solution
## Step 1: Log in as bandit8.
```bash
└─$ ssh bandit8@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit8@bandit.labs.overthewire.org's password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
## Step 2: We need to find out the unique line in `data.txt`. Let's sort the lines in `data.txt`, then we can filter out the unique line in `data.txt`.
```bash
# pipe the sorted linse from data.tx, then use uniq to filter out the unique line
bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
## Step 3: `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR` is the password. 
