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

(UNKNOWN) [192.168.0.30] 80 (http) open : Operation now in progress
the flag on this machine is a non well known tcp port following a simmilar scheme as net-ssh-02 ports but higher
you must connect to it somehow

(UNKNOWN) [192.168.0.40] 80 (http) open : Operation now in progress
this machine has access to the 172.16.0.0/24 network
need t find alternate sshd port to progress

ssh net2_student9@localhost -p 20901 -L 20902:192.168.0.10:22



























