String vs Integer
String

my_string = "Hello World"

Number

int = 1234

float = 3.14

hex = 0x45

Built-In Functions
int()

len()

str()

sum()

print()

Built-In Methods
my_string.upper()

my_string.lower()

my_string.split()

my_list.append()

my_list.insert()

How Imports Work
import {module}

import {module} as {name}

from {module} import *

from {module} import {function}

from {module} import {function} as {name}

Network Programming with Python3
tcp socket
Network Programming with Python3
Network sockets primarily use the Python3 Socket library and socket.socket function.

import socket
  s = socket.socket(socket.FAMILY, socket.TYPE, socket.PROTOCOL)
Python3 Libraries and References
Socket

Errors

Struct

Exceptions

Sys

How Imports Work
import {module}

import {module} as {name}

from {module} import *

from {module} import {function}

from {module} import {function} as {name}

Network sockets primarily use the Python3 Socket library and socket.socket function.

import socket
  s = socket.socket(socket.FAMILY, socket.TYPE, socket.PROTOCOL)

Inside the socket.socket. function, you have these arguments, in order:

socket.socket( *family*, *type*, *proto* )
family: AF_INET*, AF_INET6, AF_UNIX

type: SOCK_STREAM*, SOCK_DGRAM, SOCK_RAW

proto: 0*, IPPROTO_TCP, IPPROTO_UDP, IPPROTO_IP, IPPROTO_ICMP, IPPROTO_RAW


Understanding Python Terminology
Libraries (Standard Python Library)

Modules (_import module)

Functions (module.function)

Exceptions (try:)

Constants (AF_INET)

Objects ()

List [] vs Tuple ()


    ls
    mkdir PYSC
    cd PYSC/
    ls
    vim STREAMSHOCK.py
    file STREAMSHOCK.py
    chmod x+ STREAMSHOCK.py
    ls-lisa
    ./STREAMSHOCK.py

# Stream Socket Sender Demo

    #!/usr/bin/python3
    import socket
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0)
    ip_addr = '127.0.0.1'
    port = 1111
    s.connect((ip_addr, port))
    message = b"Message"
    s.send(message)
    data, conn = s.recvfrom(1024)
    print(data.decode('utf-8'))
    s.close()

# Stream Socket Receiver Demo

    #!/usr/bin/python3
    import socket
    import os
    port = 1111
    message = b"Connected to TCP Server on port %i\n" % port
    s = socket.socket(socket.AF_INET, socket.SOCK_STREAM, 0)
    s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
    s.bind(('', port))
    s.listen(1)
    os.system("clear")
    print ("Waiting for TCP connections\n")
    while 1:
        conn, addr = s.accept()
        connect = conn.recv(1024)
        address, port = addr
        print ("Message Received - '%s'" % connect.decode())
        print ("Sent by -", address, "port -", port, "\n")
        conn.sendall(message)
        conn.close()

# Datagram Socket Sender Demo

    #!/usr/bin/python3
    import socket
    s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM, 0)
    ip_addr = '127.0.0.1'
    port = 2222
    message = b"Message"
    s.sendto(message, (ip_addr, port))
    data, addr = s.recvfrom(1024)
    print(data.decode())
