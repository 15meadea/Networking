ip[8] <= 64 or ip6[7] <= 64 ==== all packets with a ttl of 64 and less, utilizing the IPv4 or IPv6 Headers

sudo tcpdump -n "ip[6] & 0x40 != 0" -r /home/activity_resources/pcaps/BPFCheck.pcap | wc -l ===== all IPv4 packets with at least the Dont Fragment bit set

tcp[0:2]>1024||udp[0:2]>1024 =====   traffic with a Source Port higher than 1024, utilizing the correct Transport Layer Headers

ip[9]=0x11||ip6[6]=0x11 =====  all Packets with UDP protocol being set, utilizing the IPv4 or IPv6 Headers

tcp[13]=20||tcp[13]=17 =====  only packets with the ACK/RST or ACK/FIN flag set, utilizing the correct Transport Layer Header

ip[4:2]=213 ===== all packets with an IP ID field of 213

ether[12:2]=0x8100 ===== all traffic that contains a VLAN tag

udp[0:2]=53||udp[2:2]=53||tcp[0:2]=53||tcp[2:2]=53 ===== all DNS packets

tcp[13]=2 ===== the initial packets from a client trying to initiate a TCP connection

tcp[13]=18 ===== the response packets from a server listening on an open TCP ports

tcp[13]=4 ===== the response packets from a server with closed TCP ports

tcp[2:2]<1024||udp[2:2]<1024 ===== TCP and UDP packets sent to the well known ports
