# LAYER 1 - Physical / bits

# TDM

- each session takes a turn, using time slots, to share medium between all users

# StatTDM

- more efficient version of TDM, since it dynamically allocate time slot based on feedback from results
- based on necessity, not on time-clock, when assigning free time slots

# FDM

- medium is divided into various channels based on frequencies and each session is transmitted over a different channel, e.g. Broadband

## LAYER 2 - Data Link / frames

# MAC ADDRESS

- physical addressing system that uses 48-bit address assigned to a network interface card (NIC) by manufacturers
- first 6 digits represent manufacturer
- the second 6 digits represents the exact machine

# LLC

- logical link control
- provides connection services and allows acknowledgement of receipt of message
- allows receiver to control the amount of data it gets - increase or decrease the flow
- allows for error control functions - checksum, request retransmission of the frame

# ISOCHRONOUS

- network devices use a common reference clock source and create time slots for transmission with less overhead than sybnchronous or asynchronous methods

# SYNCHRONOUS

- network devices agree on clocking method to indicate beginning and end of frames and can use control characters or separate timing channels

# ASYNCHRONOUS

- network devices reference their own internal clocks and use start/stop bits

# DEVICES

- NIC
- bridges
- switches
- MAC addresses
- anything that relies on MAC address to identify sender and receiver
- use logic to learn which MAC addresses are attached to which ports -> LUT table
  - can be reset by simply powering off for a minute

## LAYER 3 - Network / packets

- it's all about routing via IP address
  - IP v4 or IP v6
    - dotted octed address
  - IP are not hte only ones
- logical addressing
  - IP - Internet Protocol
    - apple talk and IPX were killed by IP
    - legacy systems still use them, but it's very rare
- switching = routing
  - packet switching
    - aka routing
    - most commonly used
    - it's all graph theory applied in practice
    - every pakcet may travel through different route
  - circuit switching
    - dedicated communication line between peers
    - virtual connection
  - message switching
    - data is divided into messages which may be stored and then forwarded
    - a kind of buffer, more like email
    - store and forward
- route discovery and selection
  - which way the traffic should go?
  - routing tables
  - manually configured as a static route or dynamically through a routing protocol
    - RIP
    - OSPF
    - EIGRP
- connection services
  - augment layer 2 connection services to improve reliability
  - flow control
    - slow down/speed up data transfer
  - packet reordering
    - each packet gets numbered and be put in the right order
  - ICMP
    - Internet Control Message Protocol
    - sends error messages and operational information to an IP destination
    - ping is an example of an app that uses ICMP
    - traceroute
      - large series of pings to routers
  - routers and multi-layer switches
- bandwith usage
- multiplexing strategy

## LAYER 4 - Transport / segments for TCP, datagrams for UDP

- TCP / UDP
  - TCP
    - connection-oriented protocol
    - reliable way to transport segments across the network
    - asks for acknowledgement for every packet sent
    - SYN -> SYN-ACK -> ACK // three-way handshake
      - CLIENT: SYN / seq=x
      - SERVER: SYN-ACK / ack=x+1, seq=y
      - CLIENT: ACK / ack=y+1, seq=x+1, sends data here
  - UDP
    - connection-less protocol
    - user datagram protocol
    - unreliable way to transport segments across the network
    - sender is unaware of any datagram drops
    - audio/video streaming - no need for checks, balances, zero 3-way handshake, zero re-transmission, zero buffering, zero sequencing
- windowing
  - speed up or slowing down so that the receiver can actually handle the maximum bandwith without any buffering
- buffering
  - occurs when devices allocate memory to store segments if bandwith isn't readily available
- DEVICES
  - WAN ACCELERATORS
  - LOAD BALANCERS
  - FIREWALLS

## LAYER 5 - SESSION

- prevent data from intermingling between programs
  - cross-contamination
- session lifecycle
  - set up
    - check user credentials
    - assign numbers to identify sessions
  - maintain
    - transfer data
    - reestablish connection when it breaks
    - acknowledge receipt
  - tear down
    - ending of a session after the transfer is done or when the other party disconnects
    - can be done mutually, or when the other party disappears
- DEVICES
  - protocols and software
  - H.323, H.264
    - set up, maintain and tear down voice connection and video connection
      - skype, facetime, any real-time protocol (RTP), streaming
  - NetBIOS
    - used to share files over a network

## LAYER 6 - PRESENTATION

- formatting the data
  - text - ASCII, Unicode,
  - jpeg, mov, mp3, flac, png
  - negotiate data transfer with layer 7
- securing the data with proper encryption
  - scramble the data in transit to keep it secure from prying eyes and provide data confidentiality
  - TLS - Transport Layer Security
- DEVICES
  - scripting languages - html, php, js, python, bash
  - standard text - ascii, unicode
  - pictures
  - movie files
  - encryption algorithms - ssl, tls, et c.

## LAYER 7 - APPLICATION

- application-level services where users communicate with the computer
- file transfer
- application services
  - unites communication components from more than one network application
- SMTP / POP3 / IMAP
- service advertisement
  - sending out of announcements to other devices on the network to state the services they offer
  - active directory, et c.
- DEVICES
  - POP3 / IMAP / SMTP
  - HTTP / HTTPS
  - DNS
  - FTP / FTPS / SFTP
  - TELNET / SNMP / SSH

## WIRESHARK EXAMPLE OF ISO MODEL IN PRACTICE

## Encapsulation and Decapsulation

- a process of adding and removing encapsulations as we send data through the network as we move up or down the OSI model

- PDU
  - Protocol Data Unit
  - a single unit of information transmitted in a computer network
  - L7 PDU
- L1 - bits
- L2 - frames
- L3 - packets
- L4 - segments @ TCP / datagrams @ UDP
- L5 - data

# LAYER 4 - SEGMENTS

- TCP Header - 20 bytes
  - source ports
  - destination ports
  - sequence number
  - acknowlewdgement number
  - offset
  - reserved
  - TCP control flags
  - wondow
  - checksum
  - urgent pointer
  - mTCP (optional)
- TCP control flags

  - SYN
    - synchronize connection
  - SYN-ACK
  - ACK
  - FIN
    - tear down the virtual connection
    - always after the last packet is sent
  - RST
    - used when a client or server receives a packet that it was not expecting during the current connection
  - PSH
    - ensure the data is given priority
    - typically, at the beginning or end of transmission
    - indicated by the sender
  - URG
    - sent to the recipient and process it immediately
    - violates FIFO order

- UDP Header - 8 bytes
  - source port
  - destination port
  - length
    - how many bytes the whole UDP datagram is, including header
  - checksum

# LAYER 3 - PACKETS

- IP Header
  - version
  - length
  - type of service
  - total length
  - identifier
  - flags
  - ...

# LAYER 2 - FRAMES

- ethernet header
  - destination MAC
  - source MAC
  - EtherType
  - VLAN Tag (optional)
- payload
  - 42 bytes using VLANs
  - 46 bytes with no VLANs
- MTU - maximum transmission unit
  - 1500 bytes - that's the MAX
  - jumbo frames - up to 9000 bytes
    - have to be configured in router configs

# LAYER 1 - MEDIA

- transmitting frames with 0's and 1's over the media
- when received by the next device, it gets converted back to L2 frame
  - either sent to a proper receiver, or passed by to a gateway port
