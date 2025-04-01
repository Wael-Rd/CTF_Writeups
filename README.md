# Decrypt RSSLA:
```
Attachment: RsslA.zip
```
```
[+] extract RsslA.zip 
	- flag.txt
	- public-key.pem
RSSLA it's a hint to use openssl🔐
```

### Check for public key: public.key
```
$ openssl rsa -in public-key.pem -pubin -text -modulus
Public-Key: (640 bit)
Modulus:
    00:ae:5b:b4:f2:66:00:32:59:cf:9a:6f:52:1c:3c:
    03:41:01:76:cf:16:df:53:95:34:76:ea:e3:b2:1e:
    de:6c:3c:7b:03:bd:ca:20:b3:1c:00:67:ff:a7:97:
    e4:e9:10:59:78:73:ee:f1:13:a6:0f:ec:cd:95:de:
    b5:b2:bf:10:06:6b:e2:22:4a:ce:29:d5:32:dc:0b:
    5a:74:d2:d0:06:f1
Exponent: 65537 (0x10001)
Modulus=AE5BB4F266003259CF9A6F521C3C03410176CF16DF53953476EAE3B21EDE6C3C7B03BDCA20B31C0067FFA797E4E910597873EEF113A60FECCD95DEB5B2BF10066BE2224ACE29D532DC0B5A74D2D006F1
writing RSA key
-----BEGIN PUBLIC KEY-----
MGwwDQYJKoZIhvcNAQEBBQADWwAwWAJRAK5btPJmADJZz5pvUhw8A0EBds8W31OV
NHbq47Ie3mw8ewO9yiCzHABn/6eX5OkQWXhz7vETpg/szZXetbK/EAZr4iJKzinV
MtwLWnTS0AbxAgMBAAE=
-----END PUBLIC KEY-----
```

### Use [factordb](https://factordb.com/index.php?query=3107418240490043721350750035888567930037346022842727545720161948823206440518081504556346829671723286782437916272838033415471073108501919548529007337724822783525742386454014691736602477652346609) to factor it if it's possible.
```
Factor found: 1634733645809253848443133883865090859841783670033092312181110852389333100104508151212118167511579 X 1900871281664822113126851573935413975471896789968515493666638539088027103802104498957191261465571
```
Then we found that there are only 2 prime numbers, then this RSA key is weak for factoring attack.



### Use rsatool.py to generate private key from these 2 prime numbers.
```
$ rsatool.py -p 1634733645809253848443133883865090859841783670033092312181110852389333100104508151212118167511579 -q 1900871281664822113126851573935413975471896789968515493666638539088027103802104498957191261465571 -o priv.key
Using (p, q) to initialise RSA instance

n =
ae5bb4f266003259cf9a6f521c3c03410176cf16df53953476eae3b21ede6c3c7b03bdca20b31c00
67ffa797e4e910597873eef113a60feccd95deb5b2bf10066be2224ace29d532dc0b5a74d2d006f1

e = 65537 (0x10001)

d =
8a422e3a08a81f45185a5debbe77d81cb40c822aa0eca663f3e84ea5efd46fff858c71f2d5fb3137
d13b93532570f36d772356c23fea51d39a1e7eeb0bb7e208a614526edcb094b9cf6e260ade687c01

p =
c3eca069bc6aa1ccb8e54b2ef6048320eee72e71bc49a4a3db5cbdefeba174431f969b29548be21b

q =
e3d237a8d58eb41328c65fca337affe16835804c1b7d136bfb920a2bfe1f26670bb51d47b0242be3

Saving PEM as priv.key
```

### Let's decrypt it!!! (just openssl rsautl 🔓)
```author:Mrx0rd
$ openssl rsautl -in flag.txt -out /dev/tty -inkey priv.key -decrypt
FLAG_IS_WeAK_rSA
```

​																																																		

​																																																		''Author:Mrx0rd''
