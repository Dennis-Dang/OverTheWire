# Bandit: Level 14 -> 15
<< [Level 13 -> 14](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_13-14.md) | [Level 15 -> 16](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_15-16.md) >>

## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.

## Solution
Open up a connection using the `nc` (netcat) command on port 30000.
Then, input the password for bandit12.

```console
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14 | nc localhost 30000
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr
``` 
