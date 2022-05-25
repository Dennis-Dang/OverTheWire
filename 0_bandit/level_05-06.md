# Bandit: Level 5 -> Level 6
<< [Level 4 -> 5](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_04-05.md) | [Level 6 -> 7](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_06-07.md) >>

## Level Goal
Find the password in a file in the inhere directory which has the following properties:
- human-readable
- 1033 bytes in size
- not executable

## Solution
```console
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ find . -size 1033c -not -executable | xargs file
./maybehere07/.file2: ASCII text, with very long lines
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

You may use the `find` command with the arguments: 
- `-size` 
	- Query files based on the specified size. 'c' is the suffix used to indicate bytes.
- `-not -executable`
	- Query executable files
	- the `-not` argument is used for negation

You can also use the `file` command to find ASCII text files, which are human-readable.

Through using the `find` command alone, one file came back as a result which satisfies the requirements for it being `1033 bytes long` and `non-executable`. 
You can check this result and run an additional `file` command to see if this is an ASCII file.

However, I was not satisfied with a two-liner solution. So, I created one-liner solution through the use of pipe redirection with the `xargs` command. 
- I used `xargs` to funnel all output from the query against the command `file` so that I can view which files from my query is human-readable
	- You could do another pipe redirection into a `grep` command to match for all ASCII types, but note that not all human-readable files are of type ASCII.
- This one-liner command satisfies all three properties of the file we are looking for.
