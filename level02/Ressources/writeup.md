## level02 writeup

When we log in as user level02, we see a `level02.pcap` file in the home folder. We can download it with rsync into our computer:
```shell
$ # from our local computer:
$ VM_IP=some_ip
$ export VM_IP
$ rsync -e 'ssh -p 4242' level02@$VM_IP:/home/user/level02/level02.pcap .
```
We can then upload the .pcap file in `cloudshark.org`. \
`.pcap` files are wireshark dump files for sniffing network packets. In this file we have the following content:
```
00000000  ff fd 25                                          ..%
00000000  ff fc 25                                          ..%
00000003  ff fb 26 ff fd 18 ff fd  20 ff fd 23 ff fd 27 ff  ..&.....  ..#..'.
00000013  fd 24                                             .$
00000003  ff fe 26 ff fb 18 ff fb  20 ff fb 23 ff fb 27 ff  ..&.....  ..#..'.
00000013  fc 24                                             .$
00000015  ff fa 20 01 ff f0 ff fa  23 01 ff f0 ff fa 27 01  .. ..... #.....'.
00000025  ff f0 ff fa 18 01 ff f0                           ........
00000015  ff fa 20 00 33 38 34 30  30 2c 33 38 34 30 30 ff  .. .3840 0,38400.
00000025  f0 ff fa 23 00 53 6f 64  61 43 61 6e 3a 30 ff f0  ...#.Sod aCan:0..
00000035  ff fa 27 00 00 44 49 53  50 4c 41 59 01 53 6f 64  ..'..DIS PLAY.Sod
00000045  61 43 61 6e 3a 30 ff f0  ff fa 18 00 78 74 65 72  aCan:0.. ....xter
00000055  6d ff f0                                          m..
0000002D  ff fb 03 ff fd 01 ff fd  22 ff fd 1f ff fb 05 ff  ........ ".......
0000003D  fd 21                                             .!
00000058  ff fd 03 ff fc 01 ff fb  22 ff fa 22 03 01 00 00  ........ ".."....
00000068  03 62 03 04 02 0f 05 00  00 07 62 1c 08 02 04 09  .b...... ..b.....
00000078  42 1a 0a 02 7f 0b 02 15  0f 02 11 10 02 13 11 02  B....... ........
00000088  ff ff 12 02 ff ff ff f0  ff fb 1f ff fa 1f 00 b1  ........ ........
00000098  00 31 ff f0 ff fd 05 ff  fb 21                    .1...... .!
0000003F  ff fa 22 01 03 ff f0                              .."....
000000A2  ff fa 22 01 07 ff f0                              .."....
00000046  ff fa 21 03 ff f0 ff fb  01 ff fd 00 ff fe 22     ..!..... ......"
000000A9  ff fd 01 ff fb 00 ff fc  22                       ........ "
00000055  ff fa 22 03 03 e2 03 04  82 0f 07 e2 1c 08 82 04  .."..... ........
00000065  09 c2 1a 0a 82 7f 0b 82  15 0f 82 11 10 82 13 11  ........ ........
00000075  82 ff ff 12 82 ff ff ff  f0                       ........ .
0000007E  0d 0a 4c 69 6e 75 78 20  32 2e 36 2e 33 38 2d 38  ..Linux  2.6.38-8
0000008E  2d 67 65 6e 65 72 69 63  2d 70 61 65 20 28 3a 3a  -generic -pae (::
0000009E  66 66 66 66 3a 31 30 2e  31 2e 31 2e 32 29 20 28  ffff:10. 1.1.2) (
000000AE  70 74 73 2f 31 30 29 0d  0a 0a 01 00 77 77 77 62  pts/10). ....wwwb
000000BE  75 67 73 20 6c 6f 67 69  6e 3a 20                 ugs logi n:
000000B2  6c                                                l
000000C9  00 6c                                             .l
000000B3  65                                                e
000000CB  00 65                                             .e
000000B4  76                                                v
000000CD  00 76                                             .v
000000B5  65                                                e
000000CF  00 65                                             .e
000000B6  6c                                                l
000000D1  00 6c                                             .l
000000B7  58                                                X
000000D3  00 58                                             .X
000000B8  0d                                                .
000000D5  01                                                .
000000D6  00 0d 0a 50 61 73 73 77  6f 72 64 3a 20           ...Passw ord:
000000B9  66                                                f
000000BA  74                                                t
000000BB  5f                                                _
000000BC  77                                                w
000000BD  61                                                a
000000BE  6e                                                n
000000BF  64                                                d
000000C0  72                                                r
000000C1  7f                                                .
000000C2  7f                                                .
000000C3  7f                                                .
000000C4  4e                                                N
000000C5  44                                                D
000000C6  52                                                R
000000C7  65                                                e
000000C8  6c                                                l
000000C9  7f                                                .
000000CA  4c                                                L
000000CB  30                                                0
000000CC  4c                                                L
000000CD  0d                                                .
000000E3  00 0d 0a                                          ...
000000E6  01                                                .
000000E7  00 0d 0a 4c 6f 67 69 6e  20 69 6e 63 6f 72 72 65  ...Login  incorre
000000F7  63 74 0d 0a 77 77 77 62  75 67 73 20 6c 6f 67 69  ct..wwwb ugs logi
00000107  6e 3a 20                                          n:
```
We notice a connection attempt. The dots in decimal are actually ascii non printable characters. **7f** represents a delete and **0d** a newline. \
We can then write the password down: `ft_waNDReL0L`
```shell
$ su flag02
ft_waNDReL0L

flag02@SnowCrash:~$ getflag
Check flag.Here is your token : kooda2puivaav1idi4f57q8iq
```