# Bandit: Level 21 -> Level 22
<< [Level 20 -> 21](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_20-21.md) | [Level 22 -> 23](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_22-23.md) >>

## Level Goal
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

## Solution

1. When browsing for the cronjob, we see that there is a file named `cronjob_bandit22.sh` that is executing every minute.
```console
bandit21@bandit:~$ ls /etc/cron.d/
cronjob_bandit15_root  cronjob_bandit22  cronjob_bandit24
cronjob_bandit17_root  cronjob_bandit23  cronjob_bandit25_root
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
```
2. Upon inspecting the file's content, it seems that the password for bandit22 is outputed into a file in /tmp.
```console
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

Flag:
```console
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```
