# Section 8: Routing

52. Routing Fundamentals (OBJ. 2.2)
    - all about routers and level 3
    - layer 3 switches can handle both layer 2 and layer 3 device
    -
53. Routing Tables (OBJ. 2.2 & 5.5)
    - preventing routing loops
      - split horizon
        - prevent a route learned on one interface from being advertised back out of that same interface
        - similar to spanning tree protocol
      - poison reverse
        - causes a route receied on one interface to be advertised back out of that same interface with a metric considered to be infinite
54. Routing Protocols (OBJ. 2.2)
    - Internal
      - IGP
        - interior gateway protocol
        - operates within an autonomous systm
      - RIP
      - OSPF
      - EIGRP
    - External
      - EGP
        - exterior gateway protocol
        - operate between autonomous systems
      - BGP
    - Router Advertisement Method
      - part of every dynamic routing protocol
      - distance vectors
        - the weight is determined by how many routers have to be visited
        - sends full copy of routing table to its directly-connected neighbors at regular intervals
        - hop counts
        - example protocols
          - RIP
            - uses hop count
            - maximum hop of 15, 15 = infinite
            - updates routing tables every 30 seconds
            - easy to configure
            - runs over UDP
          - BGP
            - Border Gateway Protocol
            - uses the number of autonomous system hops instead of router hops
      - link state
        - link speed, and how quick the route is
        - bandwidth is king
        - faster convergence times
        - uses cost or other factors as metric
        - requires all routers to know about the paths that all other routers can reach in the network
        - synchronized routing tables
        - example protocols
          - OSPF
            - Open Shortest Path First
            - cost based on link speed
          - IS-IS
            - Intermediate System to Intermediate System
            - similar to OSPF, but not as popular
      - hybrid
        - EIGRP
          - hybrid of distnce vector and link state protocols
          - uses bandwidth and delay
          - proprietary to Cisco
      - hold-down timer
        - prevents updates for a specific period of time and speeds up convergence
55. Address Translation (NAT and PAT) (OBJ. 1.4)
56. Multicast Routing (OBJ. 1.4)
