# Bandit: Level 7 -> Level 8

<< [Level 6 -> 7](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_06-07.md) | [Level 8 -> 9](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_08-09.md) >>



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
