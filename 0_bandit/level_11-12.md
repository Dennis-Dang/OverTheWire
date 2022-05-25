# Bandit: Level 11 -> Level 12

<< [Level 10 -> 11](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_10-11.md) | [Level 12 -> 13](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_12-13.md) >>

## Level Goal
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

## Solution
This sounds like a classic caesar cipher problem. Since the character values are rotated by 13 positions, we need to rotate them back.
I've figured out the mapping:
```
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
N O P Q R S T U V W X Y Z A B C D E F G H I J K L M
```

From this, we know that the characters A-M transpose to N-Z and vice versa. 
Use the `tr` command to rotate the character positions.
 
```console
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

The syntax specifying both of the sets looks obfuscating at first, but let's break it down:
- Set 1 consists of the character ranges A-Z and then a-z.
 - The `tr` command concatonates these ranges together to form ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz
- Set 2 consists of concatenation of the character ranges N-Z, A-M, n-z, a-m
- Finally, putting it back to back we can see the following mapping:
```console
ABCDEFGHIJKLM NOPQRSTUVWXYZ abcdefghijklm nopqrstuvwxyz
NOPQRSTUVWXYZ ABCDEFGHIJKLM nopqrstuvwxyz abcdefghijklm
```
Note: Spaces are added to emphasize the pattern breakdown.
Hopefully this explains it better. I find that it's easier if you write each of the letters down on paper and find the pattern.
