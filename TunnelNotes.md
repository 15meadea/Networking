Entry Float IP: 10.50.20.232

"localhost" associated with 127.0.0.1



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
