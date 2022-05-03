# Section 9: Network Services

57. Network Services (OBJ. 1.6)
    - Dynamic Host Configuration Protocol
        - assigns devices with IP addresses
        - provides them
            - subnet mask
            - default gateway
            - DNS server
        - opertes over port 67 and 68
        - UDP
    - DNS
        - Domain Name System
        - converts domain names to IP addresses
        - uses hierarchical and centralized system of naming
        - UDP and TCP
            - UDP for address lookup and response
            - TCP for address zone transfer into different servers
        - port 53
    - Zone Transfer
        - sharing of information between DNS servers about which domain names they have and their associated IP addresses
    - NTP
        - Network Time Protocol
        - synchronizes clocks between systems communicating over a packet-switched, variable latency data network
        - UDP
        - port 123
58. DHCP (OBJ. 1.6)
    - avoid human errors
    - DHCP reservation
        - exclude some IP addresses from being handed out to devices unless they meet a certain condition
    - DHCP Lease
        - Discovery
        - Offer
        - Request
        - Acknowledge
    - APIPA
        - Automatic Private IP Address
        - altenrative configuration, where the admin configs it manually in case DHCP fails
    - SCOPE
        - subnet mask
        - default gateway
        - DNS server
        - lease time
    - DHCP Relay
        - forwards DHCP packets between clients and servers
        - only useful when a client and the DHCP server are NOT in the same subnet
    - IP helper
        - forwards several different kinds of UDP broadcasts across the router
        - can be used in conjunction with DHCP Relay
59. Hands-on with DHCP (OBJ. 1.6)
60. DNS (OBJ. 1.6)
61. Hands-on with DNS (OBJ. 1.6)
62. NTP (OBJ. 1.6)