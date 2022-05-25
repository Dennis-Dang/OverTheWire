# Bandit: Level 0 -> 1
<< [Level 0](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_0.md) | [Level 1 -> 2](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_01-02.md) >>

## Level Goal
Find the password to Level 1, which is stored in a file called `readme` located in the home directory. Then, use it it authenticate as the user `bandit1` to continue the game.

## Solution
By using the the `ls` command, this will list all non-hidden files within the home directory. We are able to locate that there is indeed a file called `readme`. 

(I make it a habit of using the ls command after traversing into a new directory. Confirming that the files are there before you refer to them in a command is safe practice.)

The command `cat` can be used to open the file. Generally, you would want to use this command to view short plaintext files.

Syntax: `cat filename`

```console
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

### Verifying the Password
Now that the password is obtained, we can confirm that these are the right credentials by logging in.
``` console
ssh bandit1@bandit.labs.overthewire.org -p 2220
boJ9jbbUNNfktd78OOpsqOltutMc3MY1

bandit1@bandit:~$ whoami
bandit1
```

In my future writeups for this series, I won't include the process of logging into the next level just to verify the password. This decision was made in order to keep writeups concise.
