#### Start Pivot Float: 10.50.20.84
creds: netY_studentX:passwordX (netY = Networking Class Identifier & studentX = Student Number & passwordX = Student Number)


Any system, you reach or login to, you should check the "/usr/share/cctc/" directory. This is where any/all files of interest or instructions will be provided. You should always check this directory for information, just in case.

for i in {1..254}; do (ping -c 1 172.16.82.$i | grep "bytes from" &) ; done

ss -ntlp

You will have to conduct reconnaissance within the new environment to find the questions. The CTFD is only a repository for the BASE64 converted answers.
echo "CHEESE" | base64
Q0hFRVNFCg==


When creating tunnels your authorized port ranges to utilize are NSS00 - NSS99
N = NetX (1-8)
SS = Student Number - (ie 01 - 40)
00-99 = available port forward ranges
i.e. Net1_student1 can use 10100 - 10199 and Net4_student14 can use 41400 - 41499

student@blue-internet-host-student-9:~$ ssh Sterling@10.50.23.236 -L 1111:localhost:22

student@blue-internet-host-student-9:~$ ssh Sterling@localhost -p 1111 -L 2323:10.1.2.200:23

student@blue-internet-host-student-9:~$ telnet localhost 2323

Lana@lana:~$ ssh Sterling@10.1.2.130 -R 3333:localhost:8976

student@blue-internet-host-student-9:~$ ssh Sterling@localhost -p 1111 -L 4444:localhost:3333

student@blue-internet-host-student-9:~$ ssh Lana@localhost -p 4444 -L 5555:10.2.5.20:22

student@blue-internet-host-student-9:~$ ssh Cheryl@localhost -p 5555 -L 3232:10.3.9.39:23

student@blue-internet-host-student-9:~$ telnet localhost 3232

Malory@malory:~$ ssh Cheryl@10.3.9.33 -R 6666:localhost:3597

student@blue-internet-host-student-9:~$ ssh Cheryl@localhost -p 5555 -L 7777:localhost:6666

student@blue-internet-host-student-9:~$ ssh Malory@localhost -p 7777 -D 9050

Malory@malory:~$ ss -nltp

student@blue-internet-host-student-9:~$ proxychains nc localhost 58246

![image](https://github.com/user-attachments/assets/62b49f9d-7733-430c-b27e-a80b382766c1)



tcpdump -i eth1 -s0 -vv -A port 69

salt will be in home directory

creds wil be only to easy track

----------------------------------------------------------------------------------------------------

Capstone 01

Cap2 === 10.1.1.11 - OPEN PORTS: FTP-21, Telnet-23, 1918, 80

Cap3 === 10.1.1.25 - OPEN PORTS: FTP-21, 791, 4869
There is a webservice that corresponds with the rfc that governs ipv4 header structure 791
there is a listening tcp port on this system that is waiting for connections.
build a python3 tcp stream sender and send it thu your your tunnel to say Hi.
send your message as a bytes-like object and decode the response to/from UTF-8 to get
the doble-encoed message. you can use cyber chef to help you decode the message to Human Readable message.

10.1.1.30 - OPEN PORTS: ?

Cap4 === 10.1.1.33 - OPEN PORTS: FTP-21, Telnet-23, HTTP-80
Capstone 05 is on a different network that only this system can see
it is trying to attack this box, on one of the ports associated with the W32/Blaster Worm(80,69).
Use a sniffing tool(tcpdump) to try to find the message it is trying to send.

RIPv2 is running on the 10.1.1.0/25 network try to sniff out the traffic to find out what networks its advertizing in its updates
what you find will be the ip address of the nethe ip address of the next environment pivot to access from your internet host

10.50.21.126/32
ssh is running on a higher port although it only seems to accept connections when it looks like its coming from a cisco devices ttl. try using iptables to adjust your sending ttl.
the flag for this system is the ssh port number

10.1.1.90 - OPEN PORTS: ---

10.1.1.125 - OPEN PORTS: 125/tcp locus-map

N10.1.1.126 - OPEN PORTS: ---


# Tunnel to Pivot
## student@blue-internet-host-student-9:~$ ssh net2_student9@10.50.20.84 -L 20901:localhost:22

# Telnet Tunnel to .11
## student@blue-internet-host-student-9:~$ ssh net2_student9@localhost -p 20901 -L 20923:10.1.1.11:23

# Telnet To .11
## student@blue-internet-host-student-9:~$ telnet localhost 20923
