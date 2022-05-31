# Bandit: Level 19 -> 20
<< [Level 18 -> 19](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_18-19.md) | [Level 20 -> 21](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_20-21.md) >>

## Level Goal
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.

## Solution
The password bandit20 is located in /etc/bandit_pass/bandit20. Only bandit20 has access to read from this file. However, we can bypass this with the setuid binary because it passes our commands as the user bandit20.

```console
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

