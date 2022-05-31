# Bandit: Level 12 -> Level 13
<< [Level 11 -> 12](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_11-12.md) | [Level 13 -> 14](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_13-14.md) >>

## Level Goal
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## Solution
1. Given that data.txt is a hexdump, we can use the xdd command to convert the hexdump into binary.
```console 
bandit12@bandit:/tmp/dang123$ xxd -r data.txt > data.out
```

2. Using the `file` command, we observe that this is a compressed gzip file. So, we will use gzip to decompress it with the tack command `-d`.
   Note: The file must have a suffix of .gz to decompress with gzip.
```console
bandit12@bandit:/tmp/dang123$ file data.out
data: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/dang123$ mv data.out data.gz
bandit12@bandit:/tmp/dang123$ gzip -d data.gz
bandit12@bandit:/tmp/dang123$ ls
data data.txt
```

3. Using the `file` command again, we observe that this is a bzip file. So we will use `bzip2` command with the tack command `-d` to decompress it.
```
bandit12@bandit:/tmp/dang123$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/dang123$ mv data data.bz2
bandit12@bandit:/tmp/dang123$ bzip2 -d data.bz2
bandit12@bandit:/tmp/dang123$ ls
data  data.txt
```
4. The decompressed file reveals to be a gzip file again. So, repeat step 2 again.
```console
bandit12@bandit:/tmp/dang123$ file data
data: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/dang123$ mv data data.gz
bandit12@bandit:/tmp/dang123$ gzip -d data.gz
bandit12@bandit:/tmp/dang123$ ls
data  data.txt
```
5. Using the `file` command again, we observe that this is a tar archive. So we will use the `tar` command to decompress it.
```console
bandit12@bandit:/tmp/dang123$ tar -xf data
bandit12@bandit:/tmp/dang123$ ls
data  data5.bin  data.txt
```
6. Continue unwrapping the compressed file using previous steps.
```console
bandit12@bandit:/tmp/dang123$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/dang123$ tar -xf data5.bin
bandit12@bandit:/tmp/dang123$ ls
data  data5.bin  data6.bin  data.txt
bandit12@bandit:/tmp/dang123$ tar -xf data6.bin
bandit12@bandit:/tmp/dang123$ ls
data  data5.bin  data6.bin  data8.bin  data.txt
bandit12@bandit:/tmp/dang123$ tar -xf data8.bin
bandit12@bandit:/tmp/dang123$ ls
data  data5.bin  data6.bin  data8.bin  data.txt
bandit12@bandit:/tmp/dang123$ tar -xf data8.bin
bandit12@bandit:/tmp/dang123$ ls
data  data5.bin  data6.bin  data8.bin  data.txt
bandit12@bandit:/tmp/dang123$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/dang123$ mv data8.bin data9.bin.gz
bandit12@bandit:/tmp/dang123$ gzip -d data9.bin.gz
bandit12@bandit:/tmp/dang123$ file data9.bin
data9.bin: ASCII text
```
7. The last file is in plaintext, which contains the password.
```console 
bandit12@bandit:/tmp/dang123$ cat data9.bin
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

