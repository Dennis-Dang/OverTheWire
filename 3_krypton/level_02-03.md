# Krypton: Level 2 -> 3
<< [Level 01 -> 02](https://github.com/Dennis-Dang/OverTheWire/blob/main/3_krypton/level_01-02.md) | [Level 03 -> 04](https://github.com/Dennis-Dang/OverTheWire/blob/main/3_krypton/level_03-04.md) >>

## Level Problem
Given binary encrypt, keyfile.dat (used by binary) and the encrypted password file to level 3, decode the password to get to the next level.

binary usage:<br>
- input: encrypt keyfile.dat <plaintext file>
- output: ciphertext file.
- note: keyfile.dat must be in the current working directory to function

## Solution
We can first try the standard alphbet as plaintext to see how the ciphertext shifts.
1. Create a file with only the string ABCDEFGHIJKLMNOPQRSTUVWXYZ
- echo ABCDEFGHIJKLMNOPQRSTUVWXYZ > plaintext
2. Encrypt the plaintext file (assumed keyfile.dat is already in your current working directory)
- /krypton/krypton2/encrypt ./plaintext
3. Check the ciphertext
- cat ciphertext
  MNOPQRSTUVWXYZABCDEFGHIJKL
  
<br>Here, we can deduce that ABCDEFGHIJKLMNOPQRSTUVWXYZ maps to MNOPQRSTUVWXYZABCDEFGHIJKL.
- This can help us decrypt the password file (krypton3).
  
We can use the tr binary to replace sets of characters to the mapping that we found before.
- cat /krypton/krypton2/krypton3 | tr "[MNOPQRSTUVWXYZABCDEFGHIJKL]" [A-Z]
  
## Flag
CAESARISEASY
