# Problem description: https://overthewire.org/wargames/bandit/bandit16.html
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

# Solution
## Log in as bandit15
```bash
$ ssh bandit15@bandit.labs.overthewire.org -p 2220
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames

bandit15@bandit.labs.overthewire.org's password: BfMYroe26WYalil77FoDi9qh59eK5xNr
```
## We need to send current password  `BfMYroe26WYalil77FoDi9qh59eK5xNr` over to 30001 on localhost using SSL encryption. We can use `openssl s_client connect`. Note that we should use `-quiet` or `-ign_eof`. Otherwise, connection will close before the response comes back.
```bash
bandit15@bandit:~$ echo "BfMYroe26WYalil77FoDi9qh59eK5xNr" | openssl s_client -connect localhost:30001 -quiet
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

bandit15@bandit:~$ echo "BfMYroe26WYalil77FoDi9qh59eK5xNr" | openssl s_client -connect localhost:30001 -ign_eof
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
MIICBjCCAW+gAwIBAgIEfftLGTANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjEwNDEzMDgzODA3WhcNMjIwNDEzMDgzODA3WjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBAMLfXBVa
jVKDHlA3U+S0hBMJMJlfue3xKECpmx1Ajp4/khUuWwvPB7+wLjqasBO2WfFYJzcq
z9t7FfAPIlYjgvOTQs5X4vQ1aGzanvnNn+1VknpOnFAJQBSFq6ZD3ipWrhwm9XZq
8CgFhTGp9IPthZp8Y0B7OgobhlMtXD/zLaTbAgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBAMFH9rsZovwnb5k71/MpyCnXEwGlIhixUu6qfi1kiFvhJ6lJCvaO
weOYxV4oJy1OEB0LSEAQOnSPfzC8dDasijFcdVhuIGGPuQ2GZ05nCiiIZUNnrMRB
0z2RuRxgxMVjOvcSIJyvwyjVH4jY4I434fMyldePLxO1POLd1cxoKNTO
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
    Session-ID: 4DA2A4F410171FFEB8319427F4FE829701CD047218806729FCAE770F3216DF0A
    Session-ID-ctx: 
    Master-Key: 2C2BBFE4A2A4DEB821582533CBEB06BE8C646B5861F45860766079F915A22506E50305A2C97A81E84366F94B318E2199
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - f2 5b 83 7e f0 ca 58 ca-aa f3 8f 83 b9 65 d5 23   .[.~..X......e.#
    0010 - 6d 41 3f 3d 02 4e a7 37-e3 28 62 03 93 58 0c ee   mA?=.N.7.(b..X..
    0020 - 89 65 58 5b 0e 69 e5 e5-34 dd 56 4d 4b e1 b3 9e   .eX[.i..4.VMK...
    0030 - da bb 57 55 45 8f c5 7e-f8 a6 64 be 02 bc c3 a3   ..WUE..~..d.....
    0040 - 6b 7a 35 84 a1 02 c9 91-b1 95 91 bf 32 8d e8 19   kz5.........2...
    0050 - d0 38 d9 97 1a a4 24 b9-92 0d 2c a7 bf 70 d6 de   .8....$...,..p..
    0060 - 60 bb 9c 75 80 b5 38 3b-36 90 3e 95 67 5d 3d 32   `..u..8;6.>.g]=2
    0070 - 2a 82 41 ec 39 8d d8 41-18 50 93 cf 37 fe 10 c4   *.A.9..A.P..7...
    0080 - a7 29 50 ef fd 0d f7 21-03 2d cf 1e 5f 0a bd 7d   .)P....!.-.._..}
    0090 - c5 16 53 d4 44 2e 59 12-57 77 01 c9 6c d8 6d 2d   ..S.D.Y.Ww..l.m-

    Start Time: 1619407492
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed

```
