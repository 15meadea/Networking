Entry Float IP: 10.50.20.232

"localhost" associated with 127.0.0.1
super secret sauce
for i in {1..254} ;do (ping -c 1 192.168.1.$i | grep "bytes from" &) ;done

ss -ntlp ----- shows ports


Set up dynamic tunnel
ssh Sokka@10.50.20.250 -D 9050 -NT

tunnel to aang
ssh Sokka@10.50.20.250 -L 1111:192.168.1.39:22 -NT

tunnel to sokka
ssh Aang@localhost -p 1111 -L 2222:10.0.0.50:22 -NT

tunnel to toph
ssh Katara@localhost -p 2222 -L 3333:172.16.1.8:22 -NT

set up new dynamic tunnel
ssh Toph@localhost -p 3333 -D 9050



DTC: Task 3-4 Start Flags
Task 3 - Donovian Tunnels Training: dig_dug_dig_dug
Your Network Number is N (Given by Instructor)
Credentials: net{N}_studentX:passwordX
X is your student number
T3 (Atropia) Float IP address is - 10.50.27.164
T4 (Pineland) Float IP address is - 10.50.29.131 (Note - You can only telnet here to act as an insider, this will not be a routed path)
Task 4 - Donovian Data Collection: Will open when Task 3 is complete
T5 Float IP address is - 10.50.28.46
Credentials: Same as Task 3.


proxychains wget -r http://10.3.0.27
proxychains wget -r ftp://10.3.0.1

Float IP - 10.50.24.223

telent FLOATIP
ssh student@10.50.29.239 -R 2233:localhost:22
ssh Rick@localhost -p 2233 -L 1111:10.1.2.18:22
ssh Rick@localhost -p 2233 -L 2244:10.1.2.18:2222
ssh Morty@localhost -p 2244 -L 2255:172.16.10.121:2323
ssh Jerry@localhost -p 2255 -L 2266:192.168.10.69:22
ssh beth@localhost -p 2266 -D 9050
ss -ntlp
proxychains nc localhost 54321


10.50.29.239

10.50.28.46
data-collection-net-ssh-01
telnet 10.50.28.46
ssh student@10.50.29.239 -R 20901:localhost:22
ssh net2_student9@localhost -p 20901 -D 9050
(UNKNOWN) [192.168.0.10] 23 (telnet) open : Operation now in progress
(UNKNOWN) [192.168.0.10] 22 (ssh) open : Operation now in progress
(UNKNOWN) [192.168.0.10] 80 (http) open : Operation now in progress

(UNKNOWN) [192.168.0.20] 21 (ftp) open : Operation now in progress
(UNKNOWN) [192.168.0.20] 80 (http) open : Operation now in progress
alternate high ssh port used. use banner grabbing to pivot to next machine
(192.168.0.200)
(192.168.0.10)
(192.168.0.50)
(192.168.0.201) 



ssh student@10.50.29.239 -R 1111:localhost:8462
ssh Eric@localhost -p 1111 -L 2222:192.168.100.60:22
ssh Kenny@localhost -p 2222 -L 3333:10.90.50.140:6481
ssh Kyle@localhost -p 3333 -L 2323:172.20.21.5:23
ssh Kyle@172.20.21.4 -p 6481 -R 5555:localhost:22
ssh Kyle@localhost -p 3333 -L 6666:localhost:5555
ssh Stan@localhost -p 6666 -D 9050
proxychains nc localhost 65432

 
![ffa33438359ebe6c850ee21d02333155](https://github.com/user-attachments/assets/31f364e0-a91b-4dc3-b724-1984ad084d8c)





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



![d78ded20433ac6d8bb9413bedfb300c6](https://github.com/user-attachments/assets/ccb784e4-3db5-4b00-a995-72667797b07f)



(UNKNOWN) [192.168.0.30] 80 (http) open : Operation now in progress
the flag on this machine is a non well known tcp port following 
a simmilar scheme as net-ssh-02 ports but higher
you must connect to it somehow

(UNKNOWN) [192.168.0.40] 80 (http) open : Operation now in progress
this machine has access to the 172.16.0.0/24 network
need t find alternate sshd port to progress

(UNKNOWN) [172.16.0.60] 23 (telnet) open : Operation now in progress
(UNKNOWN) [172.16.0.60] 21 (ftp) open : Operation now in progress
(UNKNOWN) [172.16.0.60] 80 (http) open : Operation now in progress



you have entered Donovia credentials for this network are 
net2_comrade9:privet9


ssh net2_student9@localhost -p 20901 -L 20902:192.168.0.10:22




























