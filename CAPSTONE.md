#### Start Pivot Float: 10.50.20.84
creds: netY_studentX:passwordX (netY = Networking Class Identifier & studentX = Student Number & passwordX = Student Number)


Any system, you reach or login to, you should check the "/usr/share/cctc/" directory. This is where any/all files of interest or instructions will be provided. You should always check this directory for information, just in case.

for i in {1..254}; do (ping -c 1 172.16.82.$i | grep "bytes from" &) ; done

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

----------------------------------------------------------------------------------------------------

Capstone 01

10.1.1.11 - OPEN PORTS: FTP-21, Telnet-23

10.1.1.25 - OPEN PORTS: FTP-21

10.1.1.30 - OPEN PORTS: ?

10.1.1.33 - OPEN PORTS: FTP-21, Telnet-23, HTTP-80

10.1.1.90 - OPEN PORTS: ---

10.1.1.125 - OPEN PORTS: 125/tcp locus-map

10.1.1.126 - OPEN PORTS: ---



