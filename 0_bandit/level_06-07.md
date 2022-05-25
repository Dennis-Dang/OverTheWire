# Bandit: Level 6 -> Level 7
<< [Level 5 -> 6](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_05-06.md) | [Level 7 -> 8](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_07-08.md) >>

## Level Goal
Find the level 7 password stored in a file somewhere in the server given the following properties:
- Owned by user `bandit7`
- Owned by group `bandit6`
- 33 bytes in size

## Solution

We can query for files using the `find` command with the `-user`, `-group`, and the `-size` argument fields.

```console
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c
find: ‘/root’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit31-git’: Permission denied
find: ‘/lost+found’: Permission denied
...
```
This command returns the necessary queries, but our output is a little messy as it is bloated with errors due to not meeting required permissions to view through all files recursively under the root directory. To circumvent this, we can make use of Standard Streams to pipe all error output to /dev/null.

Standard Streams are denoted in such a way in UNIX:
- 0 - Standard Input
- 1 - Standard Output
- 2 - Standard Error

```console
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```
