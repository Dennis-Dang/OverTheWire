# Bandit: Level 13 -> 14
<< [Level 12 -> 13](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_12-13.md) | [Level 14 -> 15](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_14-15.md) \>\>

## Level Goal
The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on

## Solution
Using the `ssh` command, we will use the private SSH key to log in as **bandit14**
```console
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
``` 
