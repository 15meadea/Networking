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
