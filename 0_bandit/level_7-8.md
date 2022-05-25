# Bandit: Level 7 -> Level 8

<< [Level 6 -> 7](https://raw.githubusercontent.com/Dennis-Dang/OverTheWire/main/0_bandit/level_6-7.md) | [Level 8 -> 9](https://raw.githubusercontent.com/Dennis-Dang/OverTheWire/main/0_bandit/level_8-9.md) >>

## Level Goal
Find the password in the file data.txt next to the word millionth.

## Solution
Using the output from cat, we can redirect the ouptut as input into a `grep` command.
Grep is a tool that's used to parse for text within said input.
I'll use the `-w` tack because I want the search to match the whole word "millionth".

```console
bandit7@bandit:~$ cat data.txt | grep -w millionth
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
