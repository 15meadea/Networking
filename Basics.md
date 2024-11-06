http://networking-ctfd-2.server.vta:8000/user

https://net.cybbh.io/public/networking/latest/index.html

ssh student@10.50.29.239 -X
# ---- WELCOME TO CCTC NETWORKING ---- #

The map of the environment has been provided in your home directory:
    blue_range_complete.png

All activity PCAPS are provided here:
    /home/activity_resources/pcaps 

Below are a series of all the folders and commands you will use in this course.

    1. To view your IP address and interface information:
        a. current =        ip address (ip addr)
        b. deprecated =     ifconfig

    2. To view your ARP cache:
        a. current =        ip neighbor (ip nei)
        b. deprecated =     arp -a

    3. To view open TCP and UDP sockets:
        a. current = 
            i. TCP =        ss -antlp
            ii. UDP =       ss -anulp
        b. deprecated =     netstat

    4. To create, edit, or modify a file from the command line:
        a. vi =             vi <file>
        b. vim =            vim <file>
        c. nano =           nano <file>
    
    5. To view active processes:
        a. static =         ps -elf
        b. real-time =      top or htop

    6. To open file manager from the command line from X11 connection:
        a. nautilus
        b. pcmanfm

    7. Web Browsers from X11 connection:
        a. Firefox
        b. Chromium
        c. Konqueror

    8. To open images from the command line from X11 connection:
        a. Eye of Gnome =                   eog [file]
        b. Nomacs =                         nomacs [file]
        c. Eye of Mate =                    eom [file]
        d. GNU Image Manipulation Program = gimp [file]

    9. Find command:
        a. find / -iname <file pattern> 2>/dev/null
            / = starting location of search
            -iname = search for <file patter> with no case sensitivity
            <file pattern> = name of file to search for. Can use '*' as wildcards.
            2>/dev/null = send all errors to /dev/null

    10. Network scanning:
        a. nmap
            -sT = TCP Full connection
                nmap -sT 10.10.0.40 -p 21-23,80
            -sS = TCP SYN scanning
                sudo nmap -sS 10.10.0.40 -p 21-23,80
            -Pn = Disable ping sweep
                nmap -Pn -sT 10.10.0.40 -p 21-23,80
            -sU = UDP scanning
                sudo nmap -sU 10.10.0.40 -p 1000-2000
            -p- = Scan all ports
                nmap -sT 10.10.0.40 -p-
                nmap -sT 10.10.0.40 -p 1-65535
        b. zenmap
        c. netcat
            TCP: nc -nzvw1 10.10.0.40 21-23 80
            UDP: nc -unzvw1 10.10.0.40 53 69
        d. ping
            ping 10.10.0.40
        e. traceroute
            traceroute 172.16.82.106

    11. Network Utilization:
        a. iftop
        b. iptraf-ng

    12. Packet Manipulation (requires root privileges):
        a. scapy
        b. hping3
        c. yersinia     yersinia -G

    13. Packet Sniffing (requires root privileges):
        a. Wireshark
        b. tcpdump
        c. p0f
        d. tshark

    14. Banner Grabbing:
        a. netcat
            Client: nc 10.10.0.40 22
            Listener: nc -lvp 1234
        b. telnet
            telnet 10.10.0.40
            telnet 10.10.0.40 2323
            telnet localhost 1111
        c. wget
            wget -r http://10.10.0.40
            wget -r http://10.10.0.40:8080
            wget -r http://localhost:1111
            wget -r ftp://10.10.0.40
        d. curl
            curl http://10.10.0.40
            curl http://10.10.0.40:8080
            curl http://localhost:1111
            curl ftp://10.10.0.40

    15. DNS Query:
        a. whois
            whois google.com
        b. dig
            Records:
                A - IPv4
                    dig domain_name A
                AAAA - IPv6
                    dig domain_name AAAA
                NS - Name Server
                    dig domain_name NS
                SOA - Start of Authority
                    dig domain_name SOA
                MX - Mail Server
                    dig domain_name MX
                TXT - Human readable message
                    dig domain_name TXT
                AXFR - Zone Transfer
                    dig AXFR @dns_server domain_name

    16. Remote access:
        a. ssh
            ssh student@10.10.0.40
            ssh student@10.10.0.40 -p 2222
            ssh student@localhost -p 2222
        b. telnet
            telnet 10.10.0.40
            telnet 10.10.0.40 2323
            telnet localhost 1111

    17. File Transfer:
        a. scp
            scp student@10.10.0.40:/usr/share/cctc/flag.png .
            scp -P 2222 student@10.10.0.40:/usr/share/cctc/flag.png .
            scp -P 2222 student@localhost:/usr/share/cctc/flag.png .
            scp flag.png student@10.10.0.40:
            scp -P 2222 flag.png student@10.10.0.40:
            scp -P 2222 flag.png student@localhost:
        b. netcat
            nc 10.10.0.40 1234 < flag.png
            nc -lvp 1234 > flag.png
        c. ftp
            ftp 10.10.0.40
            
    18. Creating SSH Tunnels:
        a. Local Port Forward:
            ssh <user>@<server.ip> -p <alt port> -L <local bind port>:<tgt ip>:<tgt port>
        b. Remote Port Forward:
            ssh <user>@<server.ip> -p <alt port> -R <server bind port>:<tgt ip>:<tgt port>
        c. Dynamic:
            ssh <user>@<server.ip> -p <alt port> -D 9050

    19. To determine if tool or application is installed:
        a. which =              which <tool>
        b. whereis =            whereis <tool>

    20. Create a named pipe file:
        a. mknod =              mknod <file> -p
        b. mkfifo =             mkfifo <file>

    21. File and locations discussed in CCTC Networking:
        a. /etc/passwd =                List of user accounts
        b. /etc/shadow =                User password database
        c. /etc/services =              Services file
        d. /etc/os-release =            OS information
        e. /etc/ssh/ssh_config =        SSH user config 
        f. /etc/ssh/sshd_config =       SSH Daemon config
        g. ~/.ssh/known_hosts =         Public keys of all saved SSH servers
        h. /etc/snort =                 Snort directory
        i. /etc/snort/snort.conf  =     Snort config file
        j. /etc/snort/rules =           Default snort rules directory
        k. /var/log/snort =             Default snort log file directory
        l. /usr/share/cctc =            Default location of flags and files in shared environments
        m. /etc/proxychains.conf =      Proxychains config file
        n. /etc/p0f/p0f.fp =            p0f fingerprint file

    22. File descriptors:
        0 = Standard Input (STDIN)
        1 = Standard Output (STDOUT)
        2 = Standard Error (STDERR)
    
    23. Redirectors:
        > - redirect the STDOUT (1) of a command into a file.
            ls > file.txt
        >> - appends the STDOUT (1) of a command into a file. 
            echo "new data" >> file.txt
        < - redirect the STDOUT (1) of a file into a command.
            sort < input.txt
        | - redirect the STDOUT (1) of one command as STDIN (0) of another command.
            ps aux | grep ssh
        >& - redirect to a file descriptor.
            2>&1 | grep "open" - redirect STDERR(2) to STDOUT(1) the redirect the output to the command "grep"


