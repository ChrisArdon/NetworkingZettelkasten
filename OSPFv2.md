*Open Shortest Path First (OSPF) protocol states*

OSPF is a link-state routing [[protocol]] that is used to find the best path between the source and the destination [router](Router) using its own Shortest Path First. OSPF is developed by **Internet Engineering Task Force ([[IETF]])** as one of the Interior Gateway Protocol ([[IGP]]), i.e, the protocol which aims at moving the packet within a large autonomous system or routing domain. It is a network layer protocol which works on protocol number 89 and uses AD  value 110. OSPF uses multicast address **224.0.0.5** for normal communication and **224.0.0.6** for update to designated router (DR)/Backup Designated Router (BDR).
The topology information is flooded throughout the [[AS (Autonomous System)]], so that every router within the AS has a complete picture of the topology of the AS. This picture is then used to calculate end-to-end paths through the AS, normally using a variant of the [[Dijkstra Algorithm]]. Therefore, in a link-state routing protocol, the next hop address to which data is forwarded is determined by choosing the best end-to-end path to the eventual destination.

The main advantage of a link state routing protocol like OSPF is that the complete knowledge of topology allows routers to calculate routes that satisfy particular criteria. This can be useful for traffic engineering purposes, where routes can be constrained to meet particular quality of service requirements. The main disadvantage of a link state routing is that it does not scale well as more routers are added to the routing domain.


## OSPF terms
1. **Router I'd** - It is the highest active [[IP address]] present on the router. First, the highest [[loopback address]] is considered. If no loopback is configured then the highest active IP address on the interface of the router is considered. 
2. **Router priority** - It is and 8-[[bit]] value assigned to a router operating OSPF, used to elect DR and BDR in a [[broadcast]] network.
3. **Designated Router (DR)** - It is elected to minimize the number of adjacencies formed. DR distributes the LSAs to all the other routers. DR is elected in a broadcast network to which all the other routers share their DBD. In a broadcast network, the router requests for an update to DR, and DR will respond to that request with an update.
4. **Backup Designated Router (BDR)** - BDR is a backup to DR in a broadcast network. When DR goes down, BDR becomes DR and performs its functions.

**DR and BDR election*** - DR and BDR elections takes place in the broadcast network or multi-access network. Here are the criteria for the selection:
1. Router having the highest priority will be declared as DR.
2. If there is a tie in the router priority then the highest router I'd be considered. First, the highest loopback address is considered. If no loopback is configured then the highest active IP address on the interface of the router is considered. 


## OSPF states
The device operating OSPF goes through certain states. These states are:
1. **Down** - In this states, no hello package have been received on the interface. **Note** - The Downstate doesn't mean that  the interface is physically down. Here, it means that the OSPF adjacency process has not started yet.
2. **INIT** - In this state, the hello packets have been received from the other router.
3. **2WAY** - In the 2WAY state, both of the routers have received the hello packets from other routers. Bidirectional connectivity has been stablished. **Note** - In between the 2WAY state and Exstart state, the DR and BDR election takes place. 
4. **Exstart** - In this state, NULL DBD are exchanged. In this state, the master and slave elections take place. The router having the higher router I'd become the master while the other becomes the slave.  This election decides which router will send its DBD first (routers who have formed neighbourship will take part in this election).
5. **Exchange** - In this state, the actual DBDs are exchanged.
6. **Loading** - In this state, LSR, LSU, and [[LSA]] (Link State Acknowledgement) are exchanged.
7. **Full** - In this state, synchronization of all the information takes place. OSPF routing can begin only after the Full state.





# OSPF Configuration, commands, etc.
`router(config)#hostname R1`











References
- [What is Open Shortest Path First (OSPF)?](https://www.metaswitch.com/knowledge-center/reference/what-is-open-shortest-path-first-ospf)
- 