# Bandit: Level 1 -> 2
<< [Level 0](https://github.com/Dennis-Dang/OverTheWire/blob/main/3_krypton/level_0.md) | [Level 2 -> 3](https://github.com/Dennis-Dang/OverTheWire/blob/main/3_krypton/level_02-03.md) >>

## Level Problem
The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a simple rotation (ROT13). It is also in non-standard ciphertext format. When using alpha characters for cipher text it is normal to group the letters into 5 letter clusters, regardless of word boundaries. This helps obfuscate any patterns. This file has kept the plain text word boundaries and carried them to the cipher text.

krypton2 contains the following text:
YRIRY GJB CNFFJBEQ EBGGRA

## Solution
ROT13 uses the alphabetic characters A-Z, and replaces them 13 spaces further along in the alphabet.
<br><br>The conversion goes: 
- Input:  ABCDEFGHIJKLM
- Output: NOPQRSTUVWXYZ

<br>It is also true vice-versa:
- Input:  NOPQRSTUVWXYZ
- Output: ABCDEFGHIJKLM
</p>

## Flag
And so the decypted text would be:
<br>LEVEL TWO PASSWORD ROTTEN
