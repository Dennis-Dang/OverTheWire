# Bandit: Level 10 -> Level 11
<< [Level 9 -> 10](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_9-10.md) | [Level 11 -> 12](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_11-12.md) >>

## Level Goal
The password is stored in the file data.txt, which is encoded in base64. Decode it to obtain the password.

## Solution
Use the `base64` command with the `-d` tack to decode the file.

```console
bandit10@bandit:~$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
