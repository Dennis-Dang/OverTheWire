# Bandit - Level 1 -> Level 2
<< [Level 0 -> 1](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_0-1.md) | [Level 2 -> 3](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_2-3.md) >>
## Level Goal
Find the password to Level 2, which is stored in a file called `-` located in the home directory.

## Solution
Similar, to the previous solution, you may open this file with the `cat` command. 

However according to the [man page for cat](https://linux.die.net/man/1/cat): if you use cat with no arguments, or if the file name is named `-`.. It would just read from the Standard Input stream.

To circumvent this, you can specify the directory location with the name of the file:
`cat ./-`

In UNIX, directories are deliminated by slashes `/` in the order from the parent directory to its subdirectory. 
Syntax: 
`ParentDirectory/SubDirectory/../SubDirectory/File`

In this context, the period or dot `.` indicates the current path of the parent directory we are in now. So, `./-` means that I am specifying for the file named `-` under the current parent directory. 

```console
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
