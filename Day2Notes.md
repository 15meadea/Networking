Basic TCPDump options
-A = print payload in ASCII

-D = list interfaces

-i = specify capture interface

-e = print data-link headers

-X or XX = print payload in HEX and ASCII

-w = write to pcap

-r = read from pcap

-v, vv, or vvv = verbosity

-n = no inverse lookups

sudo tcpdump icmp

sudo tcpdump icmp[icmptype] = icmp-echo

sudo tcpdump -XXvvn icmp[icmptype] = icmp-echo

sudo tcpdump port 80

sudo tcpdump port 80 and tcp[tcpflags]

# BPF
tcpdump -i eth0 'ether[12:2] = 0x0806'
tcpdump -i eth1 'ip[9] = 0x06'
tcpdump -i eth0 'tcp[0:2] = 53 || tcp[2:2] = 53'
tcpdump 'ether[12:2] = 0x0800 && (tcp[2:2] != 22 && tcp[2:2] != 23)'

## BPF masking
tcpdump 'ether[12:4] & 0xffff0fff = 0x81000abc'
tcpdump 'ip[1] & 252 = 32'
tcpdump 'ip[6] & 224 != 0'
tcpdump 'tcp[13] & 0x11 = 0x11'
tcpdump 'tcp[12] & 0xf0 > 0x50'

BPFs at the Data-Link layer
Search for the destination broadcast MAC address.

'ether[0:4] = 0xffffffff && ether[4:2] = 0xffff'
'ether[0:2] = 0xffff && ether[2:2]= 0xffff && ether[4:2] = 0xffff'
Search for the source MAC address of fa:16:3e:f0:ca:fc.

'ether[6:4] = 0xfa163ef0 && ether[10:2] = 0xcafc'
'ether[6:2] = 0xfa16 && ether[8:2] = 0x3ef0 && ether[10:2] = 0xcafc'
BPFs at the Data-Link layer
Search for unicast (0x00) or multicast (0x01) MAC address.

'ether[0] & 0x01 = 0x00'
'ether[0] & 0x01 = 0x01'
'ether[6] & 0x01 = 0x00'
'ether[6] & 0x01 = 0x01'
BPFs at the Data-Link layer
Search for IPv4, ARP, VLAN Tag, and IPv6 respectively.

ether[12:2] = 0x0800
ether[12:2] = 0x0806
ether[12:2] = 0x8100
ether[12:2] = 0x86dd
BPFs at the Network layer
BPFs at the Network layer
Search for IHL greater than 5.

'ip[0] & 0x0f > 0x05'
'ip[0] & 15 > 5'
BPFs at the Transport layer
