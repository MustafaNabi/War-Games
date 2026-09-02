## Question 0
The password for the next level is stored in a file called **readme** located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

```
cat readme

```

## Question 1
The password for the next level is stored in a file called **-** located in the home directory
```
bandit1@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit2 bandit1 33 Jun 24 14:58 -
bandit1@bandit:~$ cat ./-
PK8------------------QToB
bandit1@bandit:~$ 


```

## Question 2
The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory

```
bandit2@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit3 bandit2 33 Jun 24 14:59 --spaces in this filename--
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename-- 
7ZZ------------------YJPME
bandit2@bandit:~$ 

```
## Question 3
The password for the next level is stored in a hidden file in the **inhere** directory.
```
bandit3@bandit:~$ ls -l
total 4
drwxr-xr-x 2 root root 4096 Jun 24 14:59 inhere
bandit3@bandit:~$ cat inhere/...Hiding-From-You 
xzTX----------------TWufAMq
bandit3@bandit:~$ 

```
## Question 4
The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.
```
bandit4@bandit:~$ ls -l
total 4
drwxr-xr-x 2 root root 4096 Jun 24 14:59 inhere
bandit4@bandit:~$ find . -readable -exec file {} \;
.: directory
./inhere: directory
./inhere/-file06: Non-ISO extended-ASCII text, with NEL line terminators
./inhere/-file09: data
./inhere/-file01: data
./inhere/-file08: data
./inhere/-file00: data
./inhere/-file03: data
./inhere/-file07: ASCII text
./inhere/-file02: OpenPGP Secret Key
./inhere/-file05: data
./inhere/-file04: data
./.bash_logout: ASCII text
./.profile: ASCII text
./.bashrc: ASCII text
bandit4@bandit:~$ cat ./inhere/-file07
6C7-----------------------j9yIrG
bandit4@bandit:~$ 

```
## Question 5
The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:
- human-readable
- 1033 bytes in size
- not executable
```
bandit5@bandit:~$ find . ! -executable -size 1033c -exec file {} \;
./inhere/maybehere07/.file2: ASCII text, with very long lines (1000)
bandit5@bandit:~$ cat ./inhere/maybehere07/.file2
pXa-------------------------OeSBW
bandit5@bandit:~$ 

```
## Question 6
The password for the next level is stored **somewhere on the server** and has all of the following properties:
- owned by user bandit7
- owned by group bandit6
- 33 bytes in size
```
bandit6@bandit:~$ find . -size 33c -user bandit7 -group bandit6
bandit6@bandit:~$ ls
bandit6@bandit:~$ ls -la
total 20
drwxr-xr-x   2 root root 4096 Jun 24 14:58 .
drwxr-xr-x 150 root root 4096 Jun 24 15:02 ..
-rw-r--r--   1 root root  220 Feb 13  2026 .bash_logout
-rw-r--r--   1 root root 3851 Jun 24 14:50 .bashrc
-rw-r--r--   1 root root  807 Feb 13  2026 .profile
bandit6@bandit:~$ find / -size 33c -user bandit7 -group bandit6 -type f 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
Bmnnv---------------------u9pr3E3
bandit6@bandit:~$ 

```
## Question 7
The password for the next level is stored in the file **data.txt** next to the word **millionth**
```
bandit7@bandit:~$ cat data.txt | grep -A 1 -B 1 millionth
concave	R1dX4soC45DFD825crecHDpn6oeL5S7p
millionth	VR1lj-------------------------9VKtub
often	LKdGZvIU8emEK3rwDIFdKJNnOg6q2PZp
bandit7@bandit:~$ 

```
## Question 8
The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once
```
bandit8@bandit:~$ cat data.txt | sort | uniq  -c -u
      1 EjmOSv-----------------------9T03kxl
bandit8@bandit:~$ 

```
## Question 9
The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.
```
bandit9@bandit:~$ strings data.txt  | sort
\?\-
&_##
,`jM
<SNIP>

<j[&v
<nMa
========== B0s2k--------------------------ndE3BG
========== password
========== the
[==p+
'=5G

<SNIP>

```
## Question 10
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data
```
bandit10@bandit:~$ cat data.txt | base64 -d
The password is pYfOY---------------------------v8vN5Ro
bandit10@bandit:~$ 

```
## Question 11
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
```
bandit11@bandit:~$ cat data.txt | tr "a-zA-Z" "n-za-mN-ZA-M"
The password is GROozW--------------------------kZiQxrN
bandit11@bandit:~$ 

```
## Question 12
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
```
bandit12@bandit:/tmp/tmp.70XGvbjGJw$ xxd -r data.txt | gzip -d | bzip2 -d | gzip -d | tar -xvf -
data5.bin

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ file data5.bin 
data5.bin: POSIX tar archive (GNU)

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ tar -xf data5.bin
bandit12@bandit:/tmp/tmp.70XGvbjGJw$ ls
data.txt  data5.bin  data6.bin

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ cat data6.bin | bzip2 -d | gzip -d
gzip: stdin: not in gzip format

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ cat data6.bin | bzip2 -d | file -
/dev/stdin: POSIX tar archive (GNU)

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ cat data6.bin | bzip2 -d | tar -xf -
bandit12@bandit:/tmp/tmp.70XGvbjGJw$ ls
data.txt  data5.bin  data6.bin  data8.bin

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Wed Jun 24 14:58:46 2026, max compression, from Unix, original size modulo 2^32 49

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ cat data8.bin | gzip -d | file -
/dev/stdin: ASCII text

bandit12@bandit:/tmp/tmp.70XGvbjGJw$ cat data8.bin | gzip -d | cat -
The password is qQYQi----------------------------ihF2uzk
bandit12@bandit:/tmp/tmp.70XGvbjGJw$ 

```
## Question 13
The password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.  
If you need help with this level: a hint file can be found in the home directory.  
Make sure to read the error messages as they are informative.
```
bandit13@bandit:~$ ls
HINT  sshkey.private
bandit13@bandit:~$ cat sshkey.private 
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAuCCoxSR6xDCnsm98kqan1x1JF3mfZ6kZa+BoAHetQ/91F4EKTfmE
E+Xs8yVgLhn1YL0TvyVswMzy33OeFJV/KEzef54V8yZo7jFcx+pQlOF6+BFRy+wsyLASV5
XxD/AtafdbVfLZFGTLC53kOFfT0VxokFmnTlIwRyxRJuNAWP9+fkAtbnfqkkixWqg0ZaLr
1fICYam6vb6ilmNfuiGHZyQNHeTkOKZgAaMnQW6bYlRjnkxsNNxk1pj0sT3MUQdLrPCdyh
l8rXUqZ60NZPA6X82/hJNQJR+zVghXrGmTTlU7MAHN7rTdoq4bIQtDShuZZmd5igp5OvVg
<SNIP>
SghZBBAsJW42cyenvyIdIzpVIcJpubAAAAwQDOOCoj/QwJLwXOd75KuUsfgI0Esq9vLSWl
Ds3fQGhnNMEJZfD9B/W8Xa7VClfPHDItcDoXiSgj4dQnS1JeeVBBUHXLULmKLmNLRNQjLD
0HSgyFYTpxl8tO5ZAlFRnGEwe7y9RvNeXp9zPQC2v1FTVQ2RdALiWvR4fGyDu0ER4hYiA/
WfqaBSBABkdhyWLiTBja/VncIHBZ04Bk1S9nwc0z6USyTXpTwpZIJw1O74Tjk+8X3or8WC
KN158egNsB+sEAAAAOcnVkeUBsb2NhbGhvc3QBAgMEBQ==
-----END OPENSSH PRIVATE KEY-----
bandit13@bandit:~$ 

bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
aaWecNk----------------------bJiYS65
bandit14@bandit:~$ 


```
## Questrion 14
The password for the next level can be retrieved by submitting the password of the current level to **port 30000 on localhost**.
```
bandit14@bandit:~$ nc localhost 30000 < aaWecNkG4FhxJQxz07uiwzVP6bJiYS65
-bash: aaWecNkG4FhxJQxz07uiwzVP6bJiYS65: No such file or directory
bandit14@bandit:~$ nc localhost 30000 < "aaWecNkG4FhxJQxz07uiwzVP6bJiYS65"
-bash: aaWecNkG4FhxJQxz07uiwzVP6bJiYS65: No such file or directory
bandit14@bandit:~$ nc localhost 30000
aaWec---------------------JiYS65
Correct!
pbLYuZ-------------------GqM68A7

```
## Question 15
The password for the next level can be retrieved by submitting the password of the current level to **port 30001 on localhost** using SSL/TLS encryption.

**Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.**
```
bandit15@bandit:~$ openssl s_client localhost:30001
Connecting to 127.0.0.1
CONNECTED(00000003)
Can't use SSL_get_servername
depth=0 CN=SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN=SnakeOil
verify return:1
---
Certificate chain
 0 s:CN=SnakeOil
   i:CN=SnakeOil
   a:PKEY: RSA, 4096 (bit); sigalg: sha256WithRSAEncryption
   v:NotBefore: Jun 10 03:59:50 2024 GMT; NotAfter: Jun  8 03:59:50 2034 GMT
---
Server certificate
-----BEGIN CERTIFICATE-----
MIIFBzCCAu+gAwIBAgIUBLz7DBxA0IfojaL/WaJzE6Sbz7cwDQYJKoZIhvcNAQEL
BQAwEzERMA8GA1UEAwwIU25ha2VPaWwwHhcNMjQwNjEwMDM1OTUwWhcNMzQwNjA4
MDM1OTUwWjATMREwDwYDVQQDDAhTbmFrZU9pbDCCAiIwDQYJKoZIhvcNAQEBBQAD
ggIPADCCAgoCggIBANI+P5QXm9Bj21FIPsQqbqZRb5XmSZZJYaam7EIJ16Fxedf+
jXAv4d/FVqiEM4BuSNsNMeBMx2Gq0lAfN33h+RMTjRoMb8yBsZsC063MLfXCk4p+
09gtGP7BS6Iy5XdmfY/fPHvA3JDEScdlDDmd6Lsbdwhv93Q8M6POVO9sv4HuS4t/
jEjr+NhE+Bjr/wDbyg7GL71BP1WPZpQnRE4OzoSrt5+bZVLvODWUFwinB0fLaGRk
GmI0r5EUOUd7HpYyoIQbiNlePGfPpHRKnmdXTTEZEoxeWWAaM1VhPGqfrB/Pnca+
vAJX7iBOb3kHinmfVOScsG/YAUR94wSELeY+UlEWJaELVUntrJ5HeRDiTChiVQ++
wnnjNbepaW6shopybUF3XXfhIb4NvwLWpvoKFXVtcVjlOujF0snVvpE+MRT0wacy
tHtjZs7Ao7GYxDz6H8AdBLKJW67uQon37a4MI260ADFMS+2vEAbNSFP+f6ii5mrB
18cY64ZaF6oU8bjGK7BArDx56bRc3WFyuBIGWAFHEuB948BcshXY7baf5jjzPmgz
mq1zdRthQB31MOM2ii6vuTkheAvKfFf+llH4M9SnES4NSF2hj9NnHga9V08wfhYc
x0W6qu+S8HUdVF+V23yTvUNgz4Q+UoGs4sHSDEsIBFqNvInnpUmtNgcR2L5PAgMB
AAGjUzBRMB0GA1UdDgQWBBTPo8kfze4P9EgxNuyk7+xDGFtAYzAfBgNVHSMEGDAW
gBTPo8kfze4P9EgxNuyk7+xDGFtAYzAPBgNVHRMBAf8EBTADAQH/MA0GCSqGSIb3
DQEBCwUAA4ICAQAKHomtmcGqyiLnhziLe97Mq2+Sul5QgYVwfx/KYOXxv2T8ZmcR
Ae9XFhZT4jsAOUDK1OXx9aZgDGJHJLNEVTe9zWv1ONFfNxEBxQgP7hhmDBWdtj6d
taqEW/Jp06X+08BtnYK9NZsvDg2YRcvOHConeMjwvEL7tQK0m+GVyQfLYg6jnrhx
egH+abucTKxabFcWSE+Vk0uJYMqcbXvB4WNKz9vj4V5Hn7/DN4xIjFko+nREw6Oa
/AUFjNnO/FPjap+d68H1LdzMH3PSs+yjGid+6Zx9FCnt9qZydW13Miqg3nDnODXw
+Z682mQFjVlGPCA5ZOQbyMKY4tNazG2n8qy2famQT3+jF8Lb6a4NGbnpeWnLMkIu
jWLWIkA9MlbdNXuajiPNVyYIK9gdoBzbfaKwoOfSsLxEqlf8rio1GGcEV5Hlz5S2
txwI0xdW9MWeGWoiLbZSbRJH4TIBFFtoBG0LoEJi0C+UPwS8CDngJB4TyrZqEld3
rH87W+Et1t/Nepoc/Eoaux9PFp5VPXP+qwQGmhir/hv7OsgBhrkYuhkjxZ8+1uk7
tUWC/XM0mpLoxsq6vVl3AJaJe1ivdA9xLytsuG4iv02Juc593HXYR8yOpow0Eq2T
U5EyeuFg5RXYwAPi7ykw1PW7zAPL4MlonEVz+QXOSx6eyhimp1VZC11SCg==
-----END CERTIFICATE-----
subject=CN=SnakeOil
issuer=CN=SnakeOil
---
No client certificate CA names sent
Peer signing digest: SHA256
Peer signature type: rsa_pss_rsae_sha256
Negotiated TLS1.3 group: X25519MLKEM768
---
SSL handshake has read 3191 bytes and written 1613 bytes
Verification error: self-signed certificate
---
New, TLSv1.3, Cipher is TLS_AES_256_GCM_SHA384
Protocol: TLSv1.3
Server public key is 4096 bit
This TLS version forbids renegotiation.
Compression: NONE
Expansion: NONE
No ALPN negotiated
Early data was not sent
Verify return code: 18 (self-signed certificate)
---
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 95BE5092887DFAB3C050F9B58510AB28146E07691B3203EE72D685E403DA931A
    Session-ID-ctx: 
    Resumption PSK: 39BE2A44FDBAD5BCC42CD729E0D6F284F582E4DB0D13BE8AEBA5B491137A4F5D10AF986069E860D3032227AE63214C1E
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - d3 36 31 7d b1 9c 35 85-7c 6b 2c a8 28 1c e7 d8   .61}..5.|k,.(...
    0010 - 88 4f b0 36 fb 50 0c 6c-4b 14 83 96 00 89 3e 16   .O.6.P.lK.....>.
    0020 - 8a 3f d1 a2 1f 83 67 7b-46 3f e6 7a 99 35 fd 7a   .?....g{F?.z.5.z
    0030 - 20 2b 56 2c b4 94 f0 de-28 fc f6 ed 30 c0 4a e6    +V,....(...0.J.
    0040 - ba 8b f5 c4 95 30 c3 f2-cf d5 30 ea 43 e3 a1 40   .....0....0.C..@
    0050 - 43 b6 4b 98 1a d4 65 33-17 98 e5 b7 75 28 50 c2   C.K...e3....u(P.
    0060 - cc 0c 7c 05 2a c2 4e 2a-42 c3 8e 26 2d 8a b5 b9   ..|.*.N*B..&-...
    0070 - 64 05 b6 33 7b f8 21 5c-19 c6 b8 ea 9e 89 2f f0   d..3{.!\....../.
    0080 - db 09 41 15 91 92 86 8e-7d 43 fe fe 63 32 9c f4   ..A.....}C..c2..
    0090 - db ae 37 19 4a 76 e3 fc-f6 74 a5 91 58 8b 9a dc   ..7.Jv...t..X...
    00a0 - 23 b4 70 18 ae 6c f1 6a-7a 08 f3 80 37 23 4a 0d   #.p..l.jz...7#J.
    00b0 - 42 60 be eb bf 9a 0f cf-ad a4 6c d4 e3 c6 23 58   B`........l...#X
    00c0 - 6b 51 81 12 34 a2 a0 71-30 e5 0a 08 b0 40 8c a0   kQ..4..q0....@..
    00d0 - 17 7d a5 71 02 43 6e 88-65 23 48 76 31 90 f8 a7   .}.q.Cn.e#Hv1...

    Start Time: 1788111271
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
---
Post-Handshake New Session Ticket arrived:
SSL-Session:
    Protocol  : TLSv1.3
    Cipher    : TLS_AES_256_GCM_SHA384
    Session-ID: 88B2F95E82CCE01F5F39B0F6215EEA4A7B282673D123C5AF6CCAE5304C48FD97
    Session-ID-ctx: 
    Resumption PSK: 36E740104689DA1E2916E3A14001317217E37AB3688E413408072C26614160F1F67A86C35AB6E007946374D31DDFC7B7
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 300 (seconds)
    TLS session ticket:
    0000 - d3 36 31 7d b1 9c 35 85-7c 6b 2c a8 28 1c e7 d8   .61}..5.|k,.(...
    0010 - 35 ce 67 20 5f 43 a2 5e-0f 93 58 29 6c c6 10 76   5.g _C.^..X)l..v
    0020 - af 32 50 b5 1d b7 a7 4f-f0 d3 76 be e4 dd 40 0b   .2P....O..v...@.
    0030 - 1a de 2a 9f d2 c3 dc b4-cd a8 cb 85 a8 59 db 8a   ..*..........Y..
    0040 - e2 7d fe cf 58 50 3b 4b-fd db a0 98 41 cf 7d 41   .}..XP;K....A.}A
    0050 - 58 c8 01 c2 32 62 ac 4c-ae b1 9f af c4 83 73 41   X...2b.L......sA
    0060 - 96 c0 1b 2c a6 90 f7 dc-18 16 b8 a3 dc 8a 81 0a   ...,............
    0070 - 24 69 8e 9a 7d f2 d8 36-d5 f3 b2 04 05 ba 1f 59   $i..}..6.......Y
    0080 - 16 36 a1 e8 cb 6f 90 85-17 d0 f4 84 5f 21 79 38   .6...o......_!y8
    0090 - 6e 49 ca f6 72 96 65 a4-4a 5e 43 20 dc b4 72 f0   nI..r.e.J^C ..r.
    00a0 - 68 97 20 71 98 a9 77 da-20 1b 24 fb 53 ab 23 f7   h. q..w. .$.S.#.
    00b0 - be 59 e5 a9 c3 ac f4 86-90 8c 11 4a 0f a1 22 fe   .Y.........J..".
    00c0 - 14 76 cf 25 7e a4 cd e1-c8 9e c8 cf 0a b9 a9 95   .v.%~...........
    00d0 - 11 e6 13 1f 8c 98 64 43-d3 d4 04 f0 36 20 04 b3   ......dC....6 ..

    Start Time: 1788111271
    Timeout   : 7200 (sec)
    Verify return code: 18 (self-signed certificate)
    Extended master secret: no
    Max Early Data: 0
---
read R BLOCK
pbLYu---------------------qM68A7
Correct!
kS0Hf----------------------Ga0X8V

closed
bandit15@bandit:~$ 

```
## Question 16
The credentials for the next level can be retrieved by submitting the password of the current level to **a port on localhost in the range 31000 to 32000**. First find out which of these ports have a server listening on them. Then find out which of those speak SSL/TLS and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

**Helpful note: Getting “DONE”, “RENEGOTIATING” or “KEYUPDATE”? Read the “CONNECTED COMMANDS” section in the manpage.**
```
bandit16@bandit:~$ nmap localhost -p31000-32000
Starting Nmap 7.98 ( https://nmap.org ) at 2026-08-30 17:45 +0000
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00017s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 996 closed tcp ports (conn-refused)
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds
bandit16@bandit:~$ 

bandit16@bandit:~$ for i in 31046 31518 31691 31790 31960; do echo "kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V" | openssl s_client -quiet 127.0.0.1:$i; done
Connecting to 127.0.0.1
40D7E7F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:423:
Connecting to 127.0.0.1
Can't use SSL_get_servername
depth=0 CN=SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN=SnakeOil
verify return:1
kS0Hf0u5HiXFwKMKFqXvPdOTNGGa0X8V
Connecting to 127.0.0.1
40D7E7F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:423:
Connecting to 127.0.0.1
Can't use SSL_get_servername
depth=0 CN=SnakeOil
verify error:num=18:self-signed certificate
verify return:1
depth=0 CN=SnakeOil
verify return:1
Correct!
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAABlwAAAAdzc2gtcn
NhAAAAAwEAAQAAAYEAvdSaw8j1FQ2DjtbQPGiEVtqEG5kt3g71uDlixg42vRN2MvWRVnGQ
t4k9T9tDWaisnn+6I4RCkhEzw231WA6KVc0Sd0+6/6Cp1Egp4o4l+xf5gPNo7A2OqjqN67
Hhy6I71GBjyUBnp6vEtkI3WZmZtuxpCMPyHSy7m56lipJFddKEOUCX21hNWWy2SAZQFBub
3M1hrcar5cA4pCFJ2AmjSsOP4yRbdERh3vZTGNjKe2x+ze4jf2/Y/uNdmixdaAMuD8to4Y
f7JylXL/+ohzasOYM0iNFvr8gkOOc11xuTNdbGNmu1Ff3Vp1qtJNB600EWrBt9H4xl7/WX
wEQ0/3EbpjUxGm3ZyUU5FmD4CGh1l9w4FqMD+RT9T3AVuzX8NM1FiIAkQMe0b34qF7iTjd
<SNIP>
r88E0Z0YZrWn1BzjPZr2z+3GPTcfYPM+pLPT3OgAjd7gVr7pEAAADBAN2qsjh6rfgKHiou
n+pf1TUIXLzpnY+icwYcotvfhjweF1KwowzqnNjG0olJqc5B6O2g8FbeIn3a1v/896Ynb3
WXXYs1cCXGyyWxkw5nWaSWS8GMVEpjIgvW46hnrWmDVEPuW84wsgZ1yGnL0InHq3SmGMVe
7FLVoO2LD393RW/2RcMZ8mX/SWGLst9IunzxoEHGxJObKWv6C2IgQj8zHDpuE/6TwdDeFS
3KWM+JyggnB+EEssW7Tu+N2H+3mgLNbwAAAMEA2zuReO3x3LioX2U5O2ZmawKeajDKAUWh
OmfbD3ab8psuVcllydLWQfmJmJ7xXyAEtmO2kIg6ax6AEd4PLAgDC504v+bmLPjdvSwqGk
//vONxwDY+Uy3m3oX+MHK2KRq5Zd3YJd9Px6AF5iMbyiQYA69nsBumqt04Ihe8CFYHa9uG
KLE1QobuX5Wx6cWaOsc1j61vpaYDEwMUT8LeMFqKjN1rF1LMiNENBQhtd+ikJmYYwB01/5
Pfos/2C+rbNuHjAAAADnJ1ZHlAbG9jYWxob3N0AQIDBA==
-----END OPENSSH PRIVATE KEY-----

Connecting to 127.0.0.1
40D7E7F7FF7F0000:error:0A0000F4:SSL routines:ossl_statem_client_read_transition:unexpected message:../ssl/statem/statem_clnt.c:423:
bandit16@bandit:~$ 


```
## Question 17
There are 2 files in the homedirectory: **passwords.old and passwords.new**. The password for the next level is in **passwords.new** and is the only line that has been changed between **passwords.old and passwords.new**

**NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19**
```
bandit17@bandit:~$ diff passwords.new  passwords.old 
42c42
< OQxXZjE---------------------0SZITXI
---
> qOg5pVOjPx9x9VccyYBADiT4xxyoUB8D
bandit17@bandit:~$ 

```
## Question 18
The password for the next level is stored in a file **readme** in the homedirectory. Unfortunately, someone has modified **.bashrc** to log you out when you log in with SSH.
```
omen15@omen15:~$ ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-1
bandit18@bandit.labs.overthewire.org's password: 
KpsOfPkc-------------------6dw8dxZI
omen15@omen15:~$ 
```
## Question 19
To gain access to the next level, you should use the setuid binary in the homedirectory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
```
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
4pIjc---------------------hxD6pOA
bandit19@bandit:~$ 

```
## Question 20
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21).

**NOTE:** Try connecting to your own network daemon to see if it works as you think
```
bandit20@bandit:~$ echo 4pIjcun--------------------7VhxD6pOA | nc -lvnp 12345
Listening on 0.0.0.0 12345
^Z
[1]+  Stopped                    echo 4pIjcu-------------hxD6pOA | nc -lvnp 12345
bandit20@bandit:~$ ./suconnect 12345
^Z
[2]+  Stopped                    ./suconnect 12345
bandit20@bandit:~$ fg
./suconnect 12345
^Z
[2]+  Stopped                    ./suconnect 12345
bandit20@bandit:~$ jobs
[1]-  Stopped                    echo 4pIjcun-------------hxD6pOA | nc -lvnp 12345
[2]+  Stopped                    ./suconnect 12345
bandit20@bandit:~$ fg 1
-bash: fg: warning: 1: job specification requires leading `%'
echo 4pIjcun--------------VhxD6pOA | nc -lvnp 12345
Connection received on 127.0.0.1 56692
^Z
[1]+  Stopped                    echo 4pIjcu-----------f7VhxD6pOA | nc -lvnp 12345
bandit20@bandit:~$ fg 2
-bash: fg: warning: 2: job specification requires leading `%'
./suconnect 12345
Read: 4pIjcunZ------------------G8Vf7VhxD6pOA
Password matches, sending next password
bandit20@bandit:~$ fg 1
-bash: fg: warning: 1: job specification requires leading `%'
echo 4pIjcun---------------f7VhxD6pOA | nc -lvnp 12345
bW9kBv5W------------------------ka6hY
bandit20@bandit:~$ 


```
## Question 21
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.
```
bandit21@bandit:~$ ls -l /etc/cron.d/*
-r--r----- 1 root root  47 Jun 24 14:59 /etc/cron.d/behemoth4_cleanup
-rw-r--r-- 1 root root 127 Jul  3 16:19 /etc/cron.d/clean_tmp
-rw-r--r-- 1 root root 120 Jun 24 14:58 /etc/cron.d/cronjob_bandit22
-rw-r--r-- 1 root root 122 Jun 24 14:58 /etc/cron.d/cronjob_bandit23
-rw-r--r-- 1 root root 120 Jun 24 14:59 /etc/cron.d/cronjob_bandit24
-rw-r--r-- 1 root root 188 Feb 13  2026 /etc/cron.d/e2scrub_all
-r--r----- 1 root root  48 Jun 24 15:00 /etc/cron.d/leviathan5_cleanup
-rw------- 1 root root 138 Jun 24 15:01 /etc/cron.d/manpage3_resetpw_job
-rwx------ 1 root root  52 Jun 24 15:02 /etc/cron.d/otw-tmp-dir
bandit21@bandit:~$ cat /etc/cron.d/cronjob_bandit22
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:~$ ^C
bandit21@bandit:~$ ls -l /etc/cron.d/cronjob_bandit22
-rw-r--r-- 1 root root 120 Jun 24 14:58 /etc/cron.d/cronjob_bandit22
bandit21@bandit:~$ cat /usr/bin/cronjob_bandit22.sh
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit21@bandit:~$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
RYVux2rHE---------------hx6AZQMEz
bandit21@bandit:~

```
## Question 22
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** Looking at shell scripts written by other people is a very useful skill. The script for this level is intentionally made easy to read. If you are having problems understanding what it does, try executing it to see the debug information it prints.
```
bandit22@bandit:~$ ls -l /etc/cron.d/*
-r--r----- 1 root root  47 Jun 24 14:59 /etc/cron.d/behemoth4_cleanup
-rw-r--r-- 1 root root 127 Jul  3 16:19 /etc/cron.d/clean_tmp
-rw-r--r-- 1 root root 120 Jun 24 14:58 /etc/cron.d/cronjob_bandit22
-rw-r--r-- 1 root root 122 Jun 24 14:58 /etc/cron.d/cronjob_bandit23
-rw-r--r-- 1 root root 120 Jun 24 14:59 /etc/cron.d/cronjob_bandit24
-rw-r--r-- 1 root root 188 Feb 13  2026 /etc/cron.d/e2scrub_all
-r--r----- 1 root root  48 Jun 24 15:00 /etc/cron.d/leviathan5_cleanup
-rw------- 1 root root 138 Jun 24 15:01 /etc/cron.d/manpage3_resetpw_job
-rwx------ 1 root root  52 Jun 24 15:02 /etc/cron.d/otw-tmp-dir
bandit22@bandit:~$ 

bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe8ls1326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
gKXDTAXn----------------qutUlPZrBsw
bandit22@bandit:~$ 

```
## Question 23
A program is running automatically at regular intervals from **cron**, the time-based job scheduler. Look in **/etc/cron.d/** for the configuration and see what command is being executed.

**NOTE:** This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level!

**NOTE 2:** Keep in mind that your shell script is removed once executed, so you may want to keep a copy around…
```
# Script 1

#!/bin/bash
cp -r /var/spool/bandit24 /tmp/tmp.7EnFM53S1A
chmod 777 /tmp/tmp.7EnFM53S1A/bandit24
chmod 777 /tmp/tmp.7EnFM53S1A/bandit24/*
```

```
# Script 2

#!/bin/bash
cp /etc/bandit_pass/bandit24 /tmp/tmp.7EnFM53S1A/bandit24.sh
chmod 777 /tmp/tmp.7EnFM53S1A/bandit24.sh
```

```
# Checking cron files
bandit23@bandit:~$ ls -la /etc/cron.d/*
-r--r----- 1 root root  47 Jun 24 14:59 /etc/cron.d/behemoth4_cleanup
-rw-r--r-- 1 root root 127 Jul  3 16:19 /etc/cron.d/clean_tmp
-rw-r--r-- 1 root root 120 Jun 24 14:59 /etc/cron.d/cronjob_bandit22
-rw-r--r-- 1 root root 122 Jun 24 14:59 /etc/cron.d/cronjob_bandit23
-rw-r--r-- 1 root root 120 Jun 24 14:59 /etc/cron.d/cronjob_bandit24
-rw-r--r-- 1 root root 188 Feb 13  2026 /etc/cron.d/e2scrub_all
-r--r----- 1 root root  48 Jun 24 15:01 /etc/cron.d/leviathan5_cleanup
-rw------- 1 root root 138 Jun 24 15:01 /etc/cron.d/manpage3_resetpw_job
-rwx------ 1 root root  52 Jun 24 15:03 /etc/cron.d/otw-tmp-dir


# Checking perms
bandit23@bandit:~$ cat /etc/cron.d/cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null

bandit23@bandit:~$ ls -la /usr/bin/cronjob_bandit24.sh
-rwxr-x--- 1 bandit24 bandit23 438 Jun 24 14:59 /usr/bin/cronjob_bandit24.sh

# Reading the script that cron runs.
# The script goes into /var/spool/bandit24/foo directory, runs the scripts owned 
# by bandit23 and deletes it.
bandit23@bandit:~$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

shopt -s nullglob

myname=$(whoami)

cd /var/spool/"$myname"/foo || exit 
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." ] && [ "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" "./$i")"
        if [ "${owner}" = "bandit23" ] && [ -f "$i" ]; then
            timeout -s 9 60 "./$i"
        fi
        rm -rf "./$i"
    fi
done

# Checking permissions of /var/spool/bandit24/foo. We can write and execute scripts
# in /var/spool/bandit24/foo but not read or list the contents.

bandit23@bandit:~$ mktemp -d
/tmp/tmp.7EnFM53S1A
bandit23@bandit:~$ cd /tmp/tmp.7EnFM53S1A
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -la /var/spool/bandit24/foo
ls: cannot open directory '/var/spool/bandit24/foo': Permission denied
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -la /var/spool/bandit24
total 12
dr-xr-x--- 3 bandit24 bandit23 4096 Jun 24 14:59 .
drwxr-xr-x 6 root     root     4096 Jun 24 15:03 ..
drwxrwx-wx 3 root     bandit24 4096 Sep  1 06:32 foo

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ 
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ nano 1
Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ chmod +x 1

# Script 1
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ cat 1
#!/bin/bash
cp -r /var/spool/bandit24 /tmp/tmp.7EnFM53S1A
chmod 777 /tmp/tmp.7EnFM53S1A/bandit
chmod 777 /tmp/tmp.7EnFM53S1A/bandit/*

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -la
total 4
drwx------  2 bandit23 bandit23   60 Sep  1 06:44 .
drwxrwx-wt 67 root     root     1660 Sep  1 06:46 ..
-rwxrwxr-x  1 bandit23 bandit23  134 Sep  1 06:44 1

# Make the temp directory writable by bandit24
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ chmod 777 .
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -la
total 4
drwxrwxrwx  2 bandit23 bandit23   60 Sep  1 06:44 .
drwxrwx-wt 67 root     root     1660 Sep  1 06:47 ..
-rwxrwxr-x  1 bandit23 bandit23  134 Sep  1 06:44 1
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ 


bandit23@bandit:/tmp/tmp.7EnFM53S1A$ cp 1 /var/spool/bandit24/foo
bandit23@bandit:/tmp/tmp.7EnFM53S1A$

# Inspecting after the cron runs our payload Script 1
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -la
total 4
drwxrwxrwx  3 bandit23 bandit23   80 Sep  1 06:52 .
drwxrwx-wt 71 root     root     1740 Sep  1 06:52 ..
-rwxrwxr-x  1 bandit23 bandit23  138 Sep  1 06:49 1
drwxrwxrwx  3 bandit24 bandit24   60 Sep  1 06:52 bandit24

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -l bandit24/foo/
total 4
-rwxrwxr-x 1 bandit24 bandit24 138 Sep  1 06:52 1
drwxrwxr-x 2 bandit24 bandit24  60 Sep  1 06:52 hackdir

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -l bandit24/foo/hackdir/hack.sh
-rwx---r-x 1 bandit24 bandit24 51 Sep  1 06:52 bandit24/foo/hackdir/hack.sh
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ 

# Reading hack.sh file
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -l bandit24/foo/hackdir/hack.sh
-rwx---r-x 1 bandit24 bandit24 51 Sep  1 06:52 bandit24/foo/hackdir/hack.sh
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ cat bandit24/foo/hackdir/hack.sh
cat /etc/bandit_pass/bandit24 > /tmp/bandit24_pass
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls -l /etc/bandit_pass/bandit24
-r-------- 1 bandit24 bandit24 33 Jun 24 14:58 /etc/bandit_pass/bandit24
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ 

# hack.sh copies /etc/bandit_pass/bandit24 file.
# We modify our script 1 to script 2 tp copy /etc/bandit_pass/bandit24 into cwd.

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ nano 2
Unable to create directory /home/bandit23/.local/share/nano/: No such file or directory
It is required for saving/loading search history or cursor positions.

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ chmod +x 2
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ cp 2 /var/spool/bandit24/foo

bandit23@bandit:/tmp/tmp.7EnFM53S1A$ ls
1  2  bandit24  bandit24.sh
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ cat bandit24.sh
hVQMk3lJ-------------------om7BOgVXv
bandit23@bandit:/tmp/tmp.7EnFM53S1A$ 
```
## Question 24
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.  
You do not need to create new connections each time
```
bandit24@bandit:~$ for i in {1000..1002}; do echo hVQMk3lJNsmQ7VF3ubyrNNBom7BOgVXv $i; done | nc localhost 30002
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
<SNIP>
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
Correct!
The password of user bandit25 is SoHfq------------------9a2Djx4P

bandit24@bandit:~$ 
```
## Question 25
Logging in to bandit26 from bandit25 should be fairly easy… The shell for user bandit26 is not **/bin/bash**, but something else. Find out what it is, how it works and how to break out of it.

> NOTE: if you’re a Windows user and typically use Powershell to `ssh` into bandit: Powershell is known to cause issues with the intended solution to this level. You should use command prompt instead.

```
# Enumerate Shell of Bandit26 from Bandit25
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$ ls -l /usr/bin/showtext
-rwxr-xr-x 1 root root 58 Jun 24 14:59 /usr/bin/showtext
bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
bandit25@bandit:~$ 


# If the terminal window is shrunk small enough before logging in, `more` cannot 
# fit the entire text on one screen. It pauses at the bottom of the page and waits # for user input

# SSH into Bandit26 when terminal shrinked to absolute mininum
```
![[Pasted image 20260902103149.png]]

```
# Press v to enter vi mode and then set shell variable as shown below
```
![[Pasted image 20260902103340.png]]

```
# Then do :shell to enter the shell
```

![[Pasted image 20260902103511.png]]

## Question 26
Good job getting a shell! Now hurry and grab the password for bandit27!

```
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
STJLJBRRphMxKB392CT4iOr5CbzPU9ER
bandit26@bandit:~$ 

```

## Question 27
There is a git repository at `ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo` via the port `2220`. The password for the user `bandit27-git` is the same as for the user `bandit27`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.

```
# Specify the port number 2220 after the FQDN.

omen15@omen15:/tmp/tmp.kRTguRqld6$ git clone ssh://bandit27-git@bandit.labs.overthewire.org:2220/home/bandit27-git/repo
Cloning into 'repo'...
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit27-git@bandit.labs.overthewire.org's password: 
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (3/3), done.
omen15@omen15:/tmp/tmp.kRTguRqld6$ ls
repo
omen15@omen15:/tmp/tmp.kRTguRqld6$ cd repo
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ ls
README
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ cat README 
The password to the next level is: y8Yd2ssKcp--------------RMzIGIeQ
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

```

## Question 28
There is a git repository at `ssh://bandit28-git@bandit.labs.overthewire.org/home/bandit28-git/repo` via the port `2220`. The password for the user `bandit28-git` is the same as for the user `bandit28`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```
omen15@omen15:/tmp/tmp.kRTguRqld6$ git clone ssh://bandit28-git@bandit.labs.overthewire.org:2220/home/bandit28-git/repo
Cloning into 'repo'...
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit28-git@bandit.labs.overthewire.org's password: 
remote: Enumerating objects: 9, done.
remote: Counting objects: 100% (9/9), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 9 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (9/9), done.
Resolving deltas: 100% (2/2), done.
omen15@omen15:/tmp/tmp.kRTguRqld6$ ls
repo
omen15@omen15:/tmp/tmp.kRTguRqld6$ cd repo/
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ ls
README.md
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ cat README.md 
# Bandit Notes
Some notes for level29 of bandit.

## credentials

- username: bandit29
- password: xxxxxxxxxx

omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

# Looking at git logs and commit history

men15@omen15:/tmp/tmp.kRTguRqld6/repo$ git log
commit e2e1de5396037bafb23e9bb37c12ebea9b911cfd (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jun 24 14:59:20 2026 +0000

    fix info leak

commit 2678cfadd8f2a347bc23e1ea491f702e5b184709
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jun 24 14:59:20 2026 +0000

    add missing data

commit 9530d526c22b9e6e6ae11070ef8ff8ee21eb2e02
Author: Ben Dover <noone@overthewire.org>
Date:   Wed Jun 24 14:59:20 2026 +0000

    initial commit of README.md
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git show e2e1de5396037bafb23e9bb37c12ebea9b911cfd
commit e2e1de5396037bafb23e9bb37c12ebea9b911cfd (HEAD -> master, origin/master, origin/HEAD)
Author: Morla Porla <morla@overthewire.org>
Date:   Wed Jun 24 14:59:20 2026 +0000

    fix info leak

diff --git a/README.md b/README.md
index 42331d9..5c6457b 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for level29 of bandit.
 ## credentials
 
 - username: bandit29
-- password: Em7eGtqaMySwNFjCpwzzHhLhospOcdt0
+- password: xxxxxxxxxx
 
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

```

## Question 29
There is a git repository at `ssh://bandit29-git@bandit.labs.overthewire.org/home/bandit29-git/repo` via the port `2220`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```
# THe answer is present in another branch.
# After cloning, we see that there are other branches. 
# We want clone other branches as the README.md file in master branch didn't contain anything.

omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git branch -v -a
* master                     b607fba fix username
  remotes/origin/HEAD        -> origin/master
  remotes/origin/dev         0bf8160 add data needed for development
  remotes/origin/master      b607fba fix username
  remotes/origin/sploits-dev a0e9e9c add some silly exploit, just for shit and giggles
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

# Cloing dev branch
omen15@omen15:/tmp/tmp.kRTguRqld6$ git clone -b dev ssh://bandit29-git@bandit.labs.overthewire.org:2220/home/bandit29-git/repo
Cloning into 'repo'...
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit29-git@bandit.labs.overthewire.org's password: 
Permission denied, please try again.
bandit29-git@bandit.labs.overthewire.org's password: 
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0 (from 0)
Receiving objects: 100% (16/16), done.
Resolving deltas: 100% (2/2), done.
omen15@omen15:/tmp/tmp.kRTguRqld6$ 



omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git branch -a -v
* dev                        0bf8160 add data needed for development
  remotes/origin/HEAD        -> origin/master
  remotes/origin/dev         0bf8160 add data needed for development
  remotes/origin/master      b607fba fix username
  remotes/origin/sploits-dev a0e9e9c add some silly exploit, just for shit and giggles
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ ls
code  README.md
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ cat README.md 
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: jq9Dfg------------------dH7USgX

omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

```

## Question 30
There is a git repository at `ssh://bandit30-git@bandit.labs.overthewire.org/home/bandit30-git/repo` via the port `2220`. The password for the user `bandit30-git` is the same as for the user `bandit30`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```
# After cloning the repo, we check for hidden tags or references.

omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git show-ref
929c564cd34ca667773e2eb02f74b514bc4eeebf refs/heads/master
929c564cd34ca667773e2eb02f74b514bc4eeebf refs/remotes/origin/HEAD
929c564cd34ca667773e2eb02f74b514bc4eeebf refs/remotes/origin/master
6a76bc87a774031428feb5cc910568293c335545 refs/tags/secret
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 


omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git show refs/tags/secret
82Nkym-------------------stHpfUf
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

```

## Question 31
There is a git repository at `ssh://bandit31-git@bandit.labs.overthewire.org/home/bandit31-git/repo` via the port `2220`. The password for the user `bandit31-git` is the same as for the user `bandit31`.

From your local machine (not the OverTheWire machine!), clone the repository and find the password for the next level. This needs git installed locally on your machine.
```
men15@omen15:/tmp/tmp.kRTguRqld6/repo$ cat README.md 
This time your task is to push a file to the remote repository.

Details:
    File name: key.txt
    Content: 'May I come in?'
    Branch: master

omen15@omen15:/tmp/tmp.kRTguRqld6/repo$
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ echo 'May I come in?' > key.txt

omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git add key.txt 
The following paths are ignored by one of your .gitignore files:
key.txt
hint: Use -f if you really want to add them.
hint: Disable this message with "git config advice.addIgnoredFile false"
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git add -f key.txt 
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git commit -m "adding key file""
> ^C
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git commit -m "adding key file"
[master fb65799] adding key file
 1 file changed, 1 insertion(+)
 create mode 100644 key.txt
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ git push
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|
                                                       

                      This is an OverTheWire game server. 
            More information on http://www.overthewire.org/wargames

backend: gibson-0
bandit31-git@bandit.labs.overthewire.org's password: 
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 12 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (5/5), 489 bytes | 489.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
remote: ### Attempting to validate files... ####
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
remote: Well done! Here is the password for the next level:
remote: pWuj5j----------------------8S1YvbT 
remote: 
remote: .oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.oOo.
remote: 
To ssh://bandit.labs.overthewire.org:2220/home/bandit31-git/repo
 ! [remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to 'ssh://bandit.labs.overthewire.org:2220/home/bandit31-git/repo'
omen15@omen15:/tmp/tmp.kRTguRqld6/repo$ 

```

## Question 32
After all this `git` stuff, it’s time for another escape. Good luck!
```
bandit31@bandit:~$ ls
bandit31@bandit:~$ cat /etc/passwd | grep bandit32
bandit32:x:11032:11032:bandit level 32:/home/bandit32:/home/bandit32/uppershell
bandit31@bandit:~$


WELCOME TO THE UPPERCASE SHELL
>> ls
sh: 1: LS: Permission denied
>> $SHELL
WELCOME TO THE UPPERCASE SHELL
>> $HOME
sh: 1: /home/bandit32: Permission denied
>> $PATH
sh: 1: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin: not found
>> $1
>> 1
sh: 1: 1: Permission denied
>> $2
>> $0
$ WHOAMI
sh: 1: WHOAMI: Permission denied
$ whoami
bandit33
$ /bin/bash -i
bandit33@bandit:~$ cat /etc/bandit_pass/bandit33
u4P2Cy--------------------vnFswM
bandit33@bandit:~$ 


```