# Bandit: Level 2 -> Level 3
<< [Level 1 -> Level 2](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_1-2.md) | [Level 3 -> Level 4](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_3-4.md) >>

## Level Goal
Find the password to Level 3, which is stored in a file called "spaces in this filename".

## Solution
Use the `cat` command to open the file. 

There are two ways that you can escape spaces in UNIX:
- Using single quotes
	`cat 'spaces in this filename'`
- backslash
	`cat spaces\ in\ this\ filename`

Additionally, you can use tab completion if typing the full name becomes tedious. 
For example if you just type:
`cat 'spaces`
Then if you press the Tab key, UNIX will attempt to complete the rest of the name of the file.

```console
bandit2@bandit:~$ cat 'spaces in this filename'
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
