# Problem description: https://overthewire.org/wargames/bandit/bandit13.html
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. 

# Solution
## Step 1: Log in as bandit12. 
```bash
└─$ ssh bandit12@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit12@bandit.labs.overthewire.org's password: 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
## Step 2: We know that `data.txt` is supposed to be a hexdump. But it is a text file now. So our first step is to transform it back to binary format using `xxd`.
```bash
bandit12@bandit:~$ xxd data.txt data.bin
xxd: data.bin: Permission denied
```
## Step 3: Unfortunately we don't have write permission in current directory. Let's create a new directory under `/tmp` folder and perform our operations there. 
```bash
bandit12@bandit:~$ mkdir /tmp/bandit12
bandit12@bandit:~$ xxd -r data.txt /tmp/bandit12/data.bin
bandit12@bandit:~$ cd /tmp/bandit12
bandit12@bandit:/tmp/bandit12$ ls
data.bin
bandit12@bandit:/tmp/bandit12$ file data.bin
data.bin: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```
## Step 4: `data.bin` is a gzip compressed file. Let's rename it to `data.gz`, then we can use `gzip` to decompress it. 
```bash
bandit12@bandit:/tmp/bandit12$ mv data.bin data.gz
bandit12@bandit:/tmp/bandit12$ gzip -d data.gz

gzip: data.gz: decompression OK, trailing garbage ignored
bandit12@bandit:/tmp/bandit12$ ls
data
bandit12@bandit:/tmp/bandit12$ file data
data: bzip2 compressed data, block size = 900k
```
## Step 5: Now `data` is a bzip2 compressed file. Let's rename it to `data.bz`, then use `bzip2` to decompress it. 
```bash
bandit12@bandit:/tmp/bandit12$ mv data data.bz
bandit12@bandit:/tmp/bandit12$ bzip2 -d data.bz
bandit12@bandit:/tmp/bandit12$ ls
data
bandit12@bandit:/tmp/bandit12$ file data
data: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```
## Step 6: `data` is gzip compressed data of `data4.bin`. let's rename it `data4.gz`, then we can use `gzip` to decompress it. 
```bash
bandit12@bandit:/tmp/bandit12$ mv data data4.gz
bandit12@bandit:/tmp/bandit12$ gzip -d data4.gz
bandit12@bandit:/tmp/bandit12$ ls
data4
bandit12@bandit:/tmp/bandit12$ file data4
data4: POSIX tar archive (GNU)
bandit12@bandit:/tmp/bandit12$ 
```
## Step 7: `data4` is tar archive. We can use `tar` to decompress it. 
```bash
bandit12@bandit:/tmp/bandit12$ tar -xf data4
bandit12@bandit:/tmp/bandit12$ ls
data4.tar  data5.bin
```
## Step 8: `data5.bin` is still tar file. 
```bash
bandit12@bandit:/tmp/bandit12$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/bandit12$ tar -xf data5.bin
bandit12@bandit:/tmp/bandit12$ ls
data4.tar  data5.bin  data6.bin
bandit12@bandit:/tmp/bandit12$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
```
## Step 9: `data6.bin` is supposed to be bzip2 form. Rename it to `data6.bz`, and use `bzip2` to decompress it. 
```bash
bandit12@bandit:/tmp/bandit12$ bzip2 -d data6.bz
bandit12@bandit:/tmp/bandit12$ ls
data4.tar  data5.bin  data6
```
## Step 10: Repeat the decompress process, and we finally get a text file with the password. 
```bash
bandit12@bandit:/tmp/bandit12$ file data6
data6: POSIX tar archive (GNU)
bandit12@bandit:/tmp/bandit12$ tar -xf data6
bandit12@bandit:/tmp/bandit12$ ls
data4.tar  data5.bin  data6  data8.bin
bandit12@bandit:/tmp/bandit12$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/bandit12$ mv data8.bin data8.gz
bandit12@bandit:/tmp/bandit12$ gzip -d data8.gz
bandit12@bandit:/tmp/bandit12$ ls
data4.tar  data5.bin  data6  data8
bandit12@bandit:/tmp/bandit12$ file data8
data8: ASCII text
bandit12@bandit:/tmp/bandit12$ cat data8
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
