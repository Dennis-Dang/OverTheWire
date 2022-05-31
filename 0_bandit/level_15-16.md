# Bandit: Level 15 -> Level 16
<< [Level 14 -> 15](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_14-15.md) | [Level 16 -> 17](https://github.com/Dennis-Dang/OverTheWire/blob/main/0_bandit/level_16-17.md) >>

## Level Goal
The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL encryption.

**Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…**

## Solution
Use the `s_client` command from the openssl client. 
- s_client -connect 
	- Establishes a connection to a server using SSL

```console
bandit15@bandit:~$ openssl
OpenSSL> s_client -connect localhost:30001
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIEXcVbPTANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjIwMzA5MTk0NzQyWhcNMjMwMzA5MTk0NzQyWjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBALDCas6k
DHxTRoxVISHtXOeCwJ8Sax5BZN76Hle8AH6pYTAdv9/FRssWL1xppFAtiGnFvglu
95FJvHEQirY4F0oPBTbtGU2xhzZzkWRL5Yj2C3Q2c99cyh+uWQT7sXPtB8W1osPc
YIo83YkXiArpt28474ZYdl+ohbPtP1oQHBv3AgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAC2693WiK/kXMCauf1fEg5DwuxIfm0saYKiLSceyZo1G4IggqOBO
9JCtvMIV/xRAmYEnPvJmf0JtYv+2fsicaPh9E1GRmU0vGoYDZzA7NTZOgRmHlRKe
ihh/XSGrY7tE1qU+EfizmhcB35iZ7W5INIKlu7oyBWcvk3rI4jtPQeZp
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: F1F3541BCAF455C47C12E12F4B1D5BC7E770B718B3125EB84B48F827C446DD00
    Session-ID-ctx:
    Master-Key: C9168470E2CF4BA8F582ED137B5AC11D6DF990BDCB5D5F0B2378F4C761204FECE081B6E67275B92C99FE8DF7D24449E1
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - d3 53 01 d9 4c 2e 82 50-ef 16 38 c5 d8 1b dd f2   .S..L..P..8.....
    0010 - 26 23 a6 72 be 70 a7 74-86 42 cf 2e 43 a1 ed 8b   &#.r.p.t.B..C...
    0020 - 54 20 a2 8e 94 70 0e 68-94 12 a8 de 69 b3 23 51   T ...p.h....i.#Q
    0030 - 7b 8f 3e 21 17 86 12 7e-63 78 a9 93 f6 7e f7 da   {.>!...~cx...~..
    0040 - 4d a5 67 c0 b0 e1 11 be-60 56 bc 81 4c 84 ec f9   M.g.....`V..L...
    0050 - cc 97 43 2e 47 fd 96 37-81 e2 de 59 3d 2f 1e d1   ..C.G..7...Y=/..
    0060 - 93 1e e5 cc 0f 80 5d 5c-7d 37 a6 90 74 1b 52 66   ......]\}7..t.Rf
    0070 - cd 15 82 b2 e2 ad 90 80-bb 4d 30 5f d0 91 3e 1b   .........M0_..>.
    0080 - f6 8f c1 5a 56 4b 6e e8-ca 90 da 18 67 0d 06 a1   ...ZVKn.....g...
    0090 - 89 e1 b7 1a 14 53 c2 ed-9f 17 9c 9c fc 20 48 22   .....S....... H"

    Start Time: 1653973821
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd
```
