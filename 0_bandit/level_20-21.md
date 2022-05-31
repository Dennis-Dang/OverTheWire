# Bandit: Level 20 -> Level 21
<< [Level 19 -> 20](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_19-20.md) | [Level 21 -> 22](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_21-22.md) >>

## Level Goal
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

**NOTE:** Try connecting to your own network daemon to see if it works as you think

## Solution
1. Use the `nc` command to set up a connection listening on an arbitrary port, for example 2200.
```console
bandit20@bandit:~$ nc -lzvp 2200
listening on [any] 2200 ...
```
2. Suspend the job as it's running in the background. Use CTRL + Z.
```console
^Z
[1]+  Stopped                 nc -lzvp 2200
```
3. Use the setuid program to connect to the listening port that we established on Step 1. This would be 2200.
```console
bandit20@bandit:~$ ./suconnect 2200
```
4. Suspend the job as it's running in the background. Use CTRL + Z.
```console
^Z
[2]+  Stopped                 ./suconnect 2200
```
5. Switch back to the netcat job using the `fg` command followed by the job number in suspension.
```console
bandit20@bandit:~$ fg 1
nc -lzvp 2200
connect to [127.0.0.1] from localhost [127.0.0.1] 33598

```
6. Type in the password for bandit20, so that suconnect could give you the next password for bandit21
```console
nc -lzvp 2200
connect to [127.0.0.1] from localhost [127.0.0.1] 33598
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```
7. Suspend the netcat process. Use CTRL + Z.
```console
^Z
[1]+  Stopped                 nc -lzvp 2200
```
8. Switch back to the suconnect process using the `fg` command.
- When you switched back, it resumed the process. So that means it sent the password back to our netcat process.
```console
bandit20@bandit:~$ fg 2
./suconnect 2200
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```
9. Return to the netcat process using `fg` for for the password for bandit21
```console
bandit20@bandit:~$ fg 1
nc -lzvp 2200
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
bandit20@bandit:~$
