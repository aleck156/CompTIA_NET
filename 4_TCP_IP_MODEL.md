# 1 - TCP/IP MODEL

- another model
  - TCP/IP model
  - TCP/IP stack
  - DoD Model
- alternative to OSI model
- almost all computer networks are nowadays a TCP/IP stack
- LAYERS
  - APPLICATION -> APPLICATION / PRESENTATION / SESSION
  - TRANSPORT
  - INTERNET -> NETWORK
  - NETWORK INTERFACE -> DATA LINK / PHYSICAL

# NETWORK INTERFACE LAYER 1

- describe how we're going to transmit bits across a network
- determines how the network medium is going to be used
- which type of network we're going to use

# INTERNET LAYER 2

- where data is taken and packaged into IP **datagrams**
- routing
- IP / ICMP / ARP / Reverse ARP

# TRANSPORT LAYER 3

- defines the level of service and the status of the conneciton being used by TCP, UDP or RTP

# APPLICATION LAYER 4

- dictates how programs are going to interface with the transport layer by conducting session management
- HTTP / telnet / FTP / SSH / SNMP / DNS / SMTP / SSL / TSL

# 2 - DATA TRANSFER OVER NETWORK

- port
  - a logical opening on a system representing a service or application that's listening and waiting for traffic
  - numbered from 0 to 65535
  - well-known and reserved ports
    - 0 - 1023
  - ephemeral ports
    - open for a short period of time for a predefined application
    - 1024 - 65535
- IPv4 packet - 20 bytes
  - source address
  - destination address
  - ports
  - IP flags
  - protocol

# 3 - PORTS AND PROTOCOLS

- SMB - server message block service
- FTP / 20, 21 / insecure file transfer, no encryption
- SSH / 22 / secure remote control of another machine using a text-based environment
- SFTP / 22 / secure file transfer
- telnet / 23 / insecure remote control of another machine using a text-based environment
- SMTP / 25 / ability to send emails over the network, RFC 821, 5321, from one server to another
- DNS / 53 / converts domain names to IP addresses and IP address to domain names
- DHCP / 67, 68 / autoamically provide network parameters to your clients, such as assigned IP address, subnet mask, default gateway, and the DNS server they should use
- TFPT / 69 / lightweight file transfer method for sending configuration files or network booting of an operating system
- HTTP / 80 / insecure web browsing
- POP3 / 110 / receive incoming emails, only for incoming emails, **older method**
- NTP / 123 / keep accurate time for clients on a network
- NetBIOS / 139 / file or printer sharing in a Windows network
- IMAP / 143 / **newer method** of retrieving emails which improves upon the older POP3
- SNMP / 161, 162 / collect data about network devices and monitor their status
- LDAP / 389 / directory services to your network, users and groups
- HTTPS / 443 / secure web browsing - SSL or TLS, which is SSL 3.0, end to end secure connection
- SMB / 445 / windows file and printer sharing services
- syslog / 514 / send logging data back to a centralized server
- SMTP TLS / 587 / secure and encrypted way to send emails
- IPP / 631 / Internet Printing Protocol
- LDAPS / 636 / secure directory services
- IMAP over SSL / 993 / secure and encrypted way to receive emails
- POP3 over SSL / 995 / secure and encrypted way to receive emails, still no memory of read/unread message status
- SQL / 1433 / communication from a client to the database engine - MsSQL
- SQLnet Protocol / 1521 / communication from a client to an Oracle database
- MySQL / 3306 / communication from a client to the MySQL database engine
- RDP / 3389 / graphical remote control of another client or server
- SIP / 5060, 5061 / initiate VoIP and video calls
- PostgreSQL / 5432 / PostgreSQL database engine
-

- make flashcards
  - one side - port number
  - back side - protocol name
  - roll from one side, then from the end

# 4 - FIND OPEN PORTS

- Network MAPper
  - command line tool that maps for the port
  - `nmap -sS -O 10.0.2.6 | more`
  - disable insecure stuff ASAP
- ZenMap
  - graphical version of nmap

# 5 - IP Protocol Types

- TCP
  - Transmission Control Protocol
  - layer 4 of OSI model
  - used on top of ethernet procol
  - 3-way handshake
  - windowing
- UDP
  - User Datagram Protocol
  - checksum is the only way to find if a packet is corrupt
  - fire a datagram and forget
  - streaming audio or video is its main usage
  - no accuracy!
- ICMP
  - Internet Control Message Protocol
  - communicate information about network connectivity issues back to the sender
  - error-reporting mechanism and query service
  - sends datagram to send diagnosting messages
  - used by technicians for diagnosis and hackers for scanning
- GRE
  - Generic Routing Encapsulation
  - simple and effective way to create a tunnel - GRE tunnel - over a public network
    - peer to peer between two ends of a tunnel, like VLAN
  - developed by Cisco
  - established at a router level
    - double check maximum unit size - MTU - to make sure the size is ok!
    - 1400 bytes is OK, 1512 bytes is typically the max set on network devices, so BE CAREFUL WHEN EXCEEDING THAT VALUE
  - does not provide any security or encryption
- IPSec
  - protect one or more data flows between peers
  - at a network or packet layer 3
  - TCP protocol
  - encrypted and secured
    - data confidentiality
    - data integrity
    - origin authentication
    - anti-replay
  - secured and encrypted GRE tunnel
  - heavily used in VPN
  - protocols used
    - AH - Authentication Header
      - integrity
      - authentication
      - hashes tcp/ip header and payload, then add AH header on front of that
    - ESP - Encapsulation Security Payload
      - encryption and integrity for the data packets sent over IPSec
      - added right after IP header
      - backward compatible with all devices
- connectionless vs connection-oriented
