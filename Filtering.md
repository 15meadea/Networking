# Filtering

# Common iptable options
-t - Specifies the table. (Default is filter)
-A - Appends a rule to the end of the list or below specified rule
-I - Inserts the rule at the top of the list or above specified rule
-R - Replaces a rule at the specified rule number
-D - Deletes a rule at the specified rule number
-F - Flushes the rules in the selected chain
-L - Lists the rules in the selected chain using standard formatting
-S - Lists the rules in the selected chain without standard formatting
-P - Sets the default policy for the selected chain
-n - Disables inverse lookups when listing rules
--line-numbers - Prints the rule number when listing rules
-p - Specifies the protocol
-i - Specifies the input interface
-o - Specifies the output interface
--sport - Specifies the source port
--dport - Specifies the destination port
-s - Specifies the source IP
-d - Specifies the destination IP
-j - Specifies the jump target action


# iptables syntax
iptables -t [table] -A [chain] [rules] -j [action]
Table: filter*, nat, mangle

Chain: INPUT, OUTPUT, PREROUTING, POSTROUTING, FORWARD


# iptables rules syntax
-i [ iface ]
-o [ iface ]
-s [ ip.add | network/CIDR ]
-d [ ip.add | network/CIDR ]

# iptables rules syntax
-p icmp [ --icmp-type type# { /code# } ]
-p tcp [ --sport | --dport { port1 |  port1:port2 } ]
-p tcp [ --tcp-flags SYN,ACK,PSH,RST,FIN,URG,ALL,NONE ]
-p udp [ --sport | --dport { port1 | port1:port2 } ]
-m to enable iptables extensions:
-m state --state NEW,ESTABLISHED,RELATED,UNTRACKED,INVALID
-m mac [ --mac-source | --mac-destination ] [mac]
-p [tcp|udp] -m multiport [ --dports | --sports | --ports { port1 | port1:port15 } ]
-m bpf --bytecode [ 'bytecode' ]
-m iprange [ --src-range | --dst-range { ip1-ip2 } ]

# iptables action syntax
ACCEPT - Allow the packet
REJECT - Deny the packet (send an ICMP reponse)
DROP - Deny the packet (send no response)
-j [ ACCEPT | REJECT | DROP ]

# Modify iptables
Flush table
iptables -t [table] -F
Change default policy
iptables -t [table] -P [chain] [action]
Lists rules with rule numbers
iptables -t [table] -L --line-numbers
Lists rules as commands interpreted by the system
iptables -t [table] -S
Inserts rule before Rule number
iptables -t [table] -I [chain] [rule num] [rules] -j [action]
Replaces rule at number
iptables -t [table] -R [chain] [rule num] [rules] -j [action]
Deletes rule at number
iptables -t [table] -D [chain] [rule num]


# NFTABLES

# NFTable Enhancements
One table command to replace:
iptables
ip6tables
arptables
ebtables

# NFTables families
ip - IPv4 packets
ip6 - IPv6 packets
inet - IPv4 and IPv6 packets
arp - layer 2
bridge - processing traffic/packets traversing bridges.
netdev - allows for user classification of packets - nftables passes up to the networking stack (no counterpart in iptables)

# NFTables hooks
ingress - netdev only
prerouting
input
forward
output
postrouting

# NFTables Chain-types
There are three chain types:
filter - to filter packets - can be used with arp, bridge, ip, ip6, and inet families
route - to reroute packets - can be used with ip and ipv6 families only
nat - used for Network Address Translation - used with ip and ip6 table families only

# NFTables syntax
## 1. Create the Table
nft add table [family] [table]
[family] = ip*, ip6, inet, arp, bridge and netdev.

[table] = user provided name for the table.

## 2. Create the Base Chain
nft add chain [family] [table] [chain] { type [type] hook [hook]
    priority [priority] \; policy [policy] \;}
* [chain] = User defined name for the chain.

* [type] =  can be filter, route or nat.

* [hook] = prerouting, ingress, input, forward, output or
         postrouting.

* [priority] = user provided integer. Lower number = higher
             priority. default = 0. Use "--" before
             negative numbers.

* ; [policy] ; = set policy for the chain. Can be
              accept (default) or drop.

 Use "\" to escape the ";" in bash

## 3. Create a rule in the Chain
nft add rule [family] [table] [chain] [matches (matches)] [statement]
* [matches] = typically protocol headers(i.e. ip, ip6, tcp,
            udp, icmp, ether, etc)

* (matches) = these are specific to the [matches] field.

* [statement] = action performed when packet is matched. Some
              examples are: log, accept, drop, reject,
              counter, nat (dnat, snat, masquerade)

# Rule Match options
ip [ saddr | daddr { ip | ip1-ip2 | ip/CIDR | ip1, ip2, ip3 } ]

tcp flags { syn, ack, psh, rst, fin }

tcp [ sport | dport { port1 | port1-port2 | port1, port2, port3 } ]

udp [ sport| dport { port1 | port1-port2 | port1, port2, port3 } ]

icmp [ type | code { type# | code# } ]

#Rule Match options
ct state { new, established, related, invalid, untracked }

iif [iface]

oif [iface]

----------------------------------------------------------------------------------------------------
To initiate a shutdown in 5 minutes:
sudo shutdown -r 5
To cancel the shutdown:
sudo shutdown -c





Task 1
IPTables/NFTables - Host Filtering

You are required to Setup and Test all Rules, prior to implementing any DROP Policy as you may lose connection if improperly configured. Notify Mission Command(Instructor) if connections are dropped.

IPTable Rule Definitions for T1

IPTable Rule Definitions for T3

NFTable Rule Definitions for T2

Validation of IPTables and NFTables

---------------------------------------------------------------------------------------------------------


Task 2
IPTables/NFTables - NAT

You are required to establishing NAT policies for T5 and T6 through the respective BLUE_HOST's they are attached to.

Prepare T1 for NAT Configurations

Change the Default Policy in the Filter Table for the INPUT, OUTPUT, and FORWARD chains to ACCEPT

Flush your current iptables rules.

Temporarily enable IPv4 forwarding using the /proc/sys/net/ipv4/ip_forward file

Prepare T5 for NAT Configurations

Ensure there is a Default GW entry present for 192.168.1.1

You can use sudo ip route replace default via 192.168.1.1


Prepare T2 for NAT Configurations

Change your chains to now have a policy of Accept

Flush your current nftables rules.

Temporarily enable IPv4 forwarding using the /proc/sys/net/ipv4/ip_forward file

Prepare T6 for NAT Configurations

Ensure there is a Default GW entry present for 192.168.3.1

You can use sudo ip route replace default via 192.168.3.1


---------------------------------------------------------------------------------------------------------


Task 3
Signatures

Gorgan Cyber Forces have captured targeted traffic related to specific Indicators of Compromise (IOCs) relating to Donovian Actors. They have stored the Traffic Capture on the Pivot:

/home/activity_resources/pcaps/ids.pcap

They have also provided the following syntax for utilizing Snort, their implemented IDS Signature solution:

To Capture traffic over the network using Snort:

sudo snort -D -i eth0 -l /var/log/snort/ -c /etc/snort/snort.conf

Use Snort signatures against a pcap:

sudo snort -r /home/activity_resources/pcaps/ids.pcap -c snort.rule

---------------------------------------------------------------------------------------------------------

Tools/Techniques: Wireshark, TCPDump, Open Source Research (OSR)

Prior Approvals: The Gorgan Government has mandated that all protections are required to be tested and validated prior to Droping and/or Blocking any traffic. Seek any clarifying guidance from Mission Command(Instructor), and ensure approval is received prior to moving between the different tasks.

Scheme of Maneuver:
Task 1
> Linux Ops Station
→ INTERNET_HOST
-→ BLUE_Host-1
-→ BLUE_Host-3
-→ BLUE_INT_DMZ_HOST-1

Target Section:

Pivot
Hostname: INTERNET_HOST
IP: 10.10.0.40 (Use the provided floating IP only for login from outside of the network
Creds: PROVIDED CREDENTIALS
Action: Utilize to Pivot into Gorgan Cyberspace and test filters & Rules

T1
Hostname: BLUE_Host-1
IP: 172.16.82.106
Creds: student : password
Action: Implement Host Filtering to Allow and Restrict Communications and Traffic

T2
Hostname: BLUE_Host-3
IP: 172.16.82.112
Creds: student : password
Action: Implement Host Filtering to Allow and Restrict Communications and Traffic

T3
Hostname: BLUE_INT_DMZ_HOST-1
IP: 172.16.40.10
Creds: student : password
Action: Implement Host Filtering to Allow and Restrict Communications and Traffic

T4
Hostname: (Will be provided by Mission Command)
IP: 10.50.23.190 (Will be Provided by Mission Command)
creds: studentX:passwordX (X = Student Number)
Known Ports: 25 
Action: Interrogate Target and validate Signatures

T5
Hostname: BLUE_PRIV_HOST-1
IP: 192.168.1.10
creds: student : password
Action: Allow traffic through NAT Capabilities

T6
Hostname: BLUE_PRIV_HOST-3
IP: 192.168.3.30
creds: student : password
Action: Allow traffic through NAT Capabilities

 sudo iptables -A INPUT -p tcp -m multiport --ports 22,23,3389,6010,6011,6012,57828,57826 -m state --state NEW,ESTABLISHED -j ACCEPT

sudo iptables -A INPUT -p tcp -m multiport --ports 22,23,3389 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --ports 22,23,3389 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -P INPUT DROP
sudo iptables -P OUTPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT

sudo iptables -A INPUT -p tcp -m multiport --sports 6579,4444 -j ACCEPT
sudo iptables -A INPUT -p tcp -m multiport --dports 6579,4444 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --sports 6579,4444 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m multiport --dports 6579,4444 -j ACCEPT
sudo iptables -A INPUT -p udp -m multiport --sports 6579,4444 -j ACCEPT
sudo iptables -A INPUT -p udp -m multiport --dports 6579,4444 -j ACCEPT
sudo iptables -A OUTPUT -p udp -m multiport --sports 6579,4444 -j ACCEPT
sudo iptables -A OUTPUT -p udp -m multiport --dports 6579,4444 -j ACCEPT

sudo iptables -A INPUT -p icmp --icmp-type echo-request -s 10.10.0.40 -j ACCEPT
sudo iptables -A INPUT -p icmp --icmp-type echo-reply -s 10.10.0.40 -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-request -d 10.10.0.40 -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-reply -d 10.10.0.40 -j ACCEPT

sudo iptables -A INPUT -p icmp --icmp-type echo-request -s 10.10.0.40 -d 172.16.82.106 -j ACCEPT
sudo iptables -A INPUT -p icmp --icmp-type echo-reply -s 10.10.0.40 -d 172.16.82.106 -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-request -s 172.16.82.106 -d 10.10.0.40 -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-reply -s 172.16.82.106 -d 10.10.0.40 -j ACCEPT
sudo iptables -A INPUT -p icmp --icmp-type echo-request -s 172.16.82.106 -d 10.10.0.40 -j ACCEPT
sudo iptables -A INPUT -p icmp --icmp-type echo-reply -s 172.16.82.106 -d 10.10.0.40 -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-request -s 10.10.0.40 -d 172.16.82.106 -j ACCEPT
sudo iptables -A OUTPUT -p icmp --icmp-type echo-reply -s 10.10.0.40 -d 172.16.82.106 -j ACCEPT

sudo iptables -A INPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A INPUT -p tcp --sport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --sport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
sudo iptables -A OUTPUT -p tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT




sudo snort -D -l /var/log/snort/ -c /etc/snort/snort.conf
tcp
alert icmp any any -> any any (msg:"Cows";content:"|DE AD BE EF|";sid:1000001;)
alert icmp any any -> 10.3.0.0/24 any (msg:"DMZ Ping";itype:8;icode:0;sid:1000002;)
alert ip any any -> 192.168.65.20 3389 (msg:"RDP!"; flow:to_server,established; sid:1000005;)

alert tcp any any -> any 445 (msg:"SMB/CIFS traffic detected on port 445"; flow:to_server,established; sid:1000003;)
alert tcp any any -> any 139 (msg:"SMB/CIFS traffic detected on port 139"; flow:to_server,established; sid:1000004;)













