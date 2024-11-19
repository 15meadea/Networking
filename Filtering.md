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
















