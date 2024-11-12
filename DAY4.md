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

![offensivefinishednetwork](https://github.com/user-attachments/assets/ceac322a-6cd5-461a-9e8b-d78bce738e86)

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
