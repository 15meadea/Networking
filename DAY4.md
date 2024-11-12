Network Scanning

    Port Scanning

    Network Scanning

      Network Enumeration
        Network Resource and shares
        Users and Groups
        Routing tables
        Auditing and Service settings
        Machine names
        Applications and banners
        SNMP and DNS details
        Other common services and ports
        
     Vulnerability Scanning
     
      Vulnerability Assessment
        Injection
        Broken Authentication
        Sensitive Data Exposure
        XML External Entities
        Broken Access Control
        Security Misconfiguration
        Software/Components with Known Vulnerabilities


Ping
Ping one IP:

ping 172.16.82.106 -c 1
Ping a range:

for i in {1..254}; do (ping -c 1 172.16.82.$i | grep "bytes from" &) ; done

nmap

traceroute

curl

wget 

netstat

ss

Windows: %SystemRoot%\system32\drivers\etc\services
Linux/Unix: /etc/services

Windows: systeminfo
Linux: uname -a and /etc/os-release

Windows: tasklist

Linux: ps or top
Example options useful for ps: -elf
e = Show all running processes
l = Show long format view
f = Show full format listing

which
whereis

Windows: route print
Linux: ip route (netstat -r deprecated)
VyOS: show ip route

find / -name hint* 2> /dev/null
find / -iname flag* 2> /dev/null

Windows: C:\Windows\System32\OpenSSH\sshd_config
Linux: /etc/ssh/sshd_config

arp-scan --interface=eth0 --localnet

nmap -sP -PR 172.16.82.96/27

Ping Scanning
ping -c 1 172.16.82.106

for i in {1..254}; do (ping -c 1 172.16.82.$i | grep "bytes from" &) ; done

sudo nmap -sP 172.16.82.96/27

DEV TCP Banner Grab
exec 3<>/dev/tcp/172.16.82.106/22; echo -e "" >&3; cat <&3

DEV TCP Scanning
for p in {1..1023}; do(echo >/dev/tcp/172.16.82.106/$p) >/dev/null 2>&1 && echo "$p open"; done

#!/bin/bash
echo "Enter network address (e.g. 192.168.0): "
read net
echo "Enter starting host range (e.g. 1): "
read start
echo "Enter ending host range (e.g. 254): "
read end
echo "Enter ports space-delimited (e.g. 21-23 80): "
read ports
for ((i=$start; $i<=$end; i++))
do
    nc -nvzw1 $net.$i $ports 2>&1 | grep -E 'succ|open'
done


![offensivefinishednetwork](https://github.com/user-attachments/assets/ceac322a-6cd5-461a-9e8b-d78bce738e86)

Network Forensics - Mapping
Device type (Router/host)

System Host-names

Interface names (eth0, eth1, etc)

IP address and CIDRs for all interfaces

TCP and UDP ports

MAC Address

OS type/version

Known credentials

Network Mapping Tools
Draw.io Local (Template)

Draw.io Web

Witeboard.com

Draw.Chat

SmartDraw

Ziteboard

Tutorialspoint Whiteboard

Explain Everything Whiteboard

Network Reconnaissance Section Complete
Check intel on the CTF server for new information regarding mission tasks.

Red Network Recon
×
Entry Float IP: 10.50.26.58

Your Network Number is N (Given by Instructor)

Credentials: net{2}_studentX:passwordX

X is your student number

Target Section:

T1
Hostname: networking-ctfd-2.server.vta
Record Type: TXT
IP: UNKNOWN
Ports: 53
Action: interrogate DNS records

Red Boundry Router
Hostname:
IP: 172.16.120.1
Ports: 22
Username: vyos
Password: password
Action: Use as start point and Perform Passive/Active Reconnaissance

T2
Hostname: UNKNOWN
IP: 172.16.182.110
Action: Perform Active Reconnaissance

T3
Hostname: UNKNOWN
IP: 172.16.140.33
Action: Perform Active Reconnaissance

T4
Hostname: UNKNOWN
IP: 172.16.182.106
Action: Perform Active Reconnaissance

T5
Hostname: UNKNOWN
IP: 172.16.182.114
Action: Perform Active Reconnaissance

T6
Hostname: UNKNOWN
IP: 172.16.182.118
Action: Perform Active Reconnaissance

T7
Hostname: UNKNOWN
IP: 172.16.140.35
Action: Perform Active Reconnaissance
