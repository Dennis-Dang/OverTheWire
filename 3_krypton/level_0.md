# Bandit: Level 0
[Level 1 -> 2](https://github.com/Dennis-Dang/OverTheWire/blob/main/3_krypton/level_01-02.md) >>

## Level Goal
Decode the password for level 1 which was encoded in Base64.

Password: S1JZUFRPTklTR1JFQVQ=

## Solution
There are many resources online that we can use to decrypt the password using the Base64 cipher. But if you wish to learn how to do it by hand, please read [RFC4648](https://www.rfc-editor.org/rfc/rfc4648)
- You mainly need to know the ASCII codes for the plaintext password. Then convert it to binary (octets). After, you can use that number and segmentate it into sextets (groups of 7). Use a lookup table of the binary sextet value into an ASCII value. The wikipedia page goes more in-depth about the process with some visuals [here](https://en.wikipedia.org/wiki/Base64)

## Flag
KRYPTONISGREAT
