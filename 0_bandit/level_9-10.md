# Bandit: Level 9 - 10
<< [Level 8 -> 9](https://raw.githubusercontent.com/Dennis-Dang/OverTheWire/main/0_bandit/level_8-9.md) | [Level 10 -> 11](https://raw.githubusercontent.com/Dennis-Dang/OverTheWire/main/0_bandit/level_10-11.md) >>

## Level Goal
The password is stored in the file data.txt in one of the few readable strings, preceded by serveral '=' characters.

## Solution
Use `strings` to parse and display all text from data.txt.
Then, use `grep` to find all instances of the use of the character '='

```console
bandit9@bandit:~$ strings data.txt | grep =
========== the*2i"4
=:G e
========== password
<I=zsGi
Z)========== is
A=|t&E
Zdb=
c^ LAh=3G
*SF=s
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```

In one of the lines, we see the following that looks like a password:
```console
truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
