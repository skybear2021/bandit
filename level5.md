# Problem description: https://overthewire.org/wargames/bandit/bandit5.html
The password for the next level is stored in the only human-readable file in the inhere directory. 
# Solution
## Step 1: Log in as bandit4
```bash
└─$ ssh bandit4@bandit.labs.overthewire.org -p 2220                          1 ⨯
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit4@bandit.labs.overthewire.org's password: pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
## Step 2: Locate the target file. Run `ls` first. There is a directory calle `inhere`.
```
bandit4@bandit:~$ ls
inhere
```
## Step 3: Let's find out what is in `inhere` folder. `ls -al` will help us find out all files in `inhere` folder.  
```
bandit4@bandit:~$ ls inhere/ -al
total 48
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file00
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file01
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file02
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file03
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file04
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file05
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file06
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file07
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file08
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file09
```
## Step 4: It turns out that there are 10 files. We can use `file` command to find out their file type. 
```
bandit4@bandit:~$ file inhere/*
inhere/-file00: data
inhere/-file01: data
inhere/-file02: data
inhere/-file03: data
inhere/-file04: data
inhere/-file05: data
inhere/-file06: data
inhere/-file07: ASCII text
inhere/-file08: data
inhere/-file09: data
```
## Step 5: Accordin to the output, `-file07` is the only human-readable file. Since the file name contains dash, we need to include directory while opening it. 
* If we are in `home` directory, we can do
```
bandit4@bandit:~$ pwd
/home/bandit4
bandit4@bandit:~$ cat inhere/-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
* If we are in `inhere` folder, we can do 
```
bandit4@bandit:~/inhere$ pwd
/home/bandit4/inhere
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```
