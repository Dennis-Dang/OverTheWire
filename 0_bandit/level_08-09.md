# Bandit: Level 8 -> Level 9
<< [Level 7 -> 8](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_07-08.md) | [Level 9 - 10](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_09-10.md) >>

## Level Goal
Using data.txt, find the password within it. The password displayed should be the only line of text that occurs once.

## Solution
Use the `uniq` command with the `-u` tack to only print unique lines.
- Note that the list must be sorted first, so use `sort` and redirect the output to `uniq`

```console
bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```
