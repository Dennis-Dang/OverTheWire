# Bandit: Level 3 -> Level 4
<< [Level 2 -> 3](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_2-3.md) | [Level 4 -> 5](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_4-5.md) >>

## Level Goal 
The password for Level 4 is stored in a `hidden file` under the directory `inhere`

## Solution
```console
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
bandit3@bandit:~/inhere$ cat .hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

Traverse into the directory `inhere` through using the `cd` command.
`cd inhere`

To view hidden files, you may use the `ls` command with the `-la` argument. This will view all contents in the parent directory in a long tabulated view.

There exists a file called `.hidden`
Use the `cat` command to obtain the password.

`cat .hidden`
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
