# Bandit: Level 17 -> 18

<< [Level 16 -> 17](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_16-17.md) | [Level 18 -> 19](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_18-19.md) >>

## Level Goal
There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

## Solution
Use the `diff` command to find changes between two files.
```console
bandit17@bandit:~$ diff passwords.new passwords.old
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
```

This output represents that the string `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` from the file `passwords.new` is the first entry that's different from the other file.
So, this must be the password for bandit17.
