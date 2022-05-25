# Bandit: Level 4 -> Level 5
<< [Level 3 -> 4](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_03-04.md) | [Level 5 -> 6](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_05-06.md) >>

## Level Goal
Find the password in one of the files under the directory `inhere`. Only one of them is human readable in plaintext.

## Solution
```console
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

Using the `file` command, we can determine each of the file's file type.
`file ./*`
- Note: the asterisk (\*) is a wildcard character that denotes all files within the current directory.
  - You can certainly use the `file` command for each file in the directory individually. This is just a more elegant way to invocate one single command onto multiple files.

It then shows that -file07 is an ASCII file, which is a type of plaintext file.
Using the `cat` command, we can obtain the password to Level 5.
