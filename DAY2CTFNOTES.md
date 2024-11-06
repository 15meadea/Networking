ip[8] <= 64 or ip6[7] <= 64 ==== Berkeley Packet Filter, using tcpdump, to capture all packets with a ttl of 64 and less, utilizing the IPv4 or IPv6 Headers

sudo tcpdump -n "ip[6] & 0x40 != 0" -r /home/activity_resources/pcaps/BPFCheck.pcap | wc -l ===== Berkeley Packet Filter, using tcpdump, to capture all IPv4 packets with at least the Dont Fragment bit set
