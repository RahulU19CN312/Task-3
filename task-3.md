rv@localhost:~$ ip -a
------------------------

Usage: ip [ OPTIONS ] OBJECT { COMMAND | help }
       ip [ -force ] -batch filename
where  OBJECT := { address | addrlabel | fou | help | ila | ioam | l2tp | link |
                   macsec | maddress | monitor | mptcp | mroute | mrule |
                   neighbor | neighbour | netconf | netns | nexthop | ntable |
                   ntbl | route | rule | sr | stats | tap | tcpmetrics |
                   token | tunnel | tuntap | vrf | xfrm }
       OPTIONS := { -V[ersion] | -s[tatistics] | -d[etails] | -r[esolve] |
                    -h[uman-readable] | -iec | -j[son] | -p[retty] |
                    -f[amily] { inet | inet6 | mpls | bridge | link } |
                    -4 | -6 | -M | -B | -0 |
                    -l[oops] { maximum-addr-flush-attempts } | -echo | -br[ief] |
                    -o[neline] | -t[imestamp] | -ts[hort] | -b[atch] [filename] |
                    -rc[vbuf] [size] | -n[etns] name | -N[umeric] | -a[ll] |
                    -c[olor]}


=====================================================================
rv@localhost:~$ ifconfig
---------------------------

ens33: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.74.128  netmask 255.255.255.0  broadcast 192.168.74.255
        inet6 fe80::20c:29ff:fe5b:e019  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:5b:e0:19  txqueuelen 1000  (Ethernet)
        RX packets 3994  bytes 5306726 (5.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1099  bytes 106613 (104.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 18  bytes 2112 (2.0 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 18  bytes 2112 (2.0 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

====================================================================

ping -c 4 8.8.8.8
------------------

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=128 time=44.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=128 time=30.3 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=128 time=34.6 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3019ms
rtt min/avg/max/mdev = 30.258/36.558/44.833/6.111 ms

===================================================================
ping -c 4 google.com
-------------------------

PING google.com (142.251.220.46) 56(84) bytes of data.
64 bytes from google.com (142.251.220.46): icmp_seq=1 ttl=128 time=20.1 ms
64 bytes from google.com (142.251.220.46): icmp_seq=2 ttl=128 time=25.0 ms
64 bytes from google.com (142.251.220.46): icmp_seq=4 ttl=128 time=35.1 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3066ms
rtt min/avg/max/mdev = 20.077/26.711/35.083/6.248 ms

====================================================================

rv@localhost:~$ ss -tuln
----------------------------

Netid State  Recv-Q Send-Q  Local Address:Port   Peer Address:Port 
udp   UNCONN 0      0           127.0.0.1:323         0.0.0.0:*    
udp   UNCONN 0      0             0.0.0.0:5353        0.0.0.0:*    
udp   UNCONN 0      0               [::1]:323            [::]:*    
udp   UNCONN 0      0                [::]:5353           [::]:*    
tcp   LISTEN 0      4096        127.0.0.1:631         0.0.0.0:*    
tcp   LISTEN 0      128           0.0.0.0:22          0.0.0.0:*    
tcp   LISTEN 0      50                  *:8080              *:*    
tcp   LISTEN 0      4096            [::1]:631            [::]:*    
tcp   LISTEN 0      4096                *:9090              *:*    
tcp   LISTEN 0      128              [::]:22             [::]:*

=====================================================================
rv@localhost:~$ netstat -tuln
---------------------------------

Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp6       0      0 :::8080                 :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::9090                 :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
udp        0      0 127.0.0.1:323           0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp6       0      0 ::1:323                 :::*                               
udp6       0      0 :::5353                 :::*                 

=====================================================================

rv@localhost:~$ nslookup google.com
------------------------------------

;; Got recursion not available from 192.168.74.2
Server:		192.168.74.2
Address:	192.168.74.2#53

Non-authoritative answer:
Name:	google.com
Address: 142.251.220.46
Name:	google.com
Address: 2404:6800:4009:810::200e

=================================================================

rv@localhost:~$ traceroute google.com
--------------------------------------

traceroute to google.com (142.251.220.46), 30 hops max, 60 byte packets
 1  _gateway (192.168.74.2)  2.551 ms  2.379 ms  2.198 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * *^C

=====================================================================

rv@localhost:~$ ip addr
---------------------------
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:5b:e0:19 brd ff:ff:ff:ff:ff:ff
    altname enp2s1
    altname enx000c295be019
    inet 192.168.74.128/24 brd 192.168.74.255 scope global dynamic noprefixroute ens33
       valid_lft 1554sec preferred_lft 1554sec
    inet6 fe80::20c:29ff:fe5b:e019/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

==========================================================================================

