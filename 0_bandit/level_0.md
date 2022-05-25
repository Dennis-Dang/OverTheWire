# Bandit - Level 0
[Level 0 -> 1](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_0-1.md)
## Level Goal
The goal of this level is to log into the game though using SSH. 

The following credentials are given:

`host: bandit.labs.overthewire.org`

`port: 2220`

`username: bandit0`

`password: bandit0`

## Solution:
The syntax for making an SSH connection goes like this:

`ssh username@hostname -p portNumber`

Thus, with the provided credentials:

`ssh bandit0@bandit.labs.overthewire.org -p 2220`

It should also then prompt for the password, which is:

`bandit0`

Once the connection is authenticated, we can confirm that we have sucessfully logged in by using the command `whoami`, which should tell us that this connection is logged in as bandit0.


Another way to visually see this is by looking at the bash shell's prompt:

```console
bandit0@bandit:~$
```

Most shells in UNIX has their command line formated like this on default:

`username@hostname:~$`

- The `~` means that we are at the home directory.
- The `$` means that we are authenticated as a standard user.
  - Otherwise, if you are authenticated as a superuser or sudoer you would see a `#` instead.
- You may customize this prompt by overriding $PS1 variable in the hidden .bashrc file.
  - Visit the man page for more information about its formatting under "Prompting"
