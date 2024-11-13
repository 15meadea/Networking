T2 --- 64 bytes from 172.16.182.110: icmp_seq=1 ttl=59 time=2.43 ms
T4 --- 64 bytes from 172.16.182.106: icmp_seq=1 ttl=59 time=8.32 ms
T5 --- 64 bytes from 172.16.182.114: icmp_seq=1 ttl=59 time=1.82 ms
T6 --- 64 bytes from 172.16.182.118: icmp_seq=1 ttl=59 time=2.38 ms
64 bytes from 172.16.182.126: icmp_seq=1 ttl=60 time=1.09 ms
64 bytes from 172.16.140.6: icmp_seq=1 ttl=60 time=2.35 ms
64 bytes from 172.16.140.5: icmp_seq=1 ttl=59 time=11.6 ms
T3 --- 64 bytes from 172.16.140.33: icmp_seq=1 ttl=58 time=16.4 ms
T7 --- 64 bytes from 172.16.140.35: icmp_seq=1 ttl=58 time=13.6 ms
64 bytes from 172.16.140.62: icmp_seq=1 ttl=59 time=1.27 ms
64 bytes from 172.16.120.2: icmp_seq=1 ttl=63 time=0.357 ms
BR --- 64 bytes from 172.16.120.1: icmp_seq=1 ttl=62 time=1.13 ms
64 bytes from 172.16.120.10: icmp_seq=1 ttl=62 time=0.518 ms
64 bytes from 172.16.120.18: icmp_seq=1 ttl=61 time=1.32 ms
64 bytes from 172.16.120.9: icmp_seq=1 ttl=61 time=12.7 ms
64 bytes from 172.16.120.17: icmp_seq=1 ttl=60 time=2.31 ms

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Red Boundry Router Hostname: IP: 172.16.120.1 Ports: 22 Username: vyos Password: password Action: Use as start point and Perform Passive/Active Reconnaissance

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Red Network Recon × Entry Float IP: 10.50.26.58
Your Network Number is N (Given by Instructor)
Credentials: net2_student9:password9

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
vyos@RED-SCR> show int
Codes: S - State, L - Link, u - Up, D - Down, A - Admin Down
Interface        IP Address                        S/L  Description
---------        ----------                        ---  -----------
eth0             172.16.120.1/29                   u/u  INTERNET 
eth1             172.16.120.10/29                  u/u  REDNET 
eth2             172.16.101.30/27                  u/u  DMZ 
lo               127.0.0.1/8                       u/u  
                 120.0.0.1/32
                 ::1/128

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
how to get png

wget -r 172.16.140.33

ssh net2_student9@10.50.26.58 -X

eom http://172.16.140.33/hint-01.png

