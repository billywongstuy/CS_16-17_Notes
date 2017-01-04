# 12/20/16
#Aim: Cisco in an hour™	

##Required Components of Networking
* physical connection
* identification
* protocol/ common language/ common packaging
* routing
* security
* data validation
* user experience

##OSI 7-Layer Model
  * Used to help conceptualize the different parts of network connections.
  
  * The top layer is the most concrete, with each subsequent layer becoming more abstract (
  relying less on the physical connections and more on code).
  
  * The Layers
  1. Physical
  2. Data Link
  3. Network
  4. Transport
  5. Session
  6. Presentation
  7. Application
  
  * If you are working on a particular layer, you should not have to think too much about the other layers.
  
  <b>Physical Layer</b>
  * How computers are physically connected
  * Things like electrons running across wires, radio signals pulsing through the air...
  * A brief history of wired connections
    * Thiccnet
      * A single Coaxial cable runs throughout the network, "vampire taps" go into the cable and leec the data out.
    * Thinnet
      * A single Coaxial cable runs throughout the network, T-Junctions used to splice connections
        
    * In Thicknet and Thinnet, all data is sent to all computers.
      
    * Each computer added increases the power drain on the entire system, degrading service.
    
    
# 12/21/16
#Aim: Cisco in an hour™ Part II: Electric Boogaloo

 <b>Physical Layer cont.</b>
 
 * Token Ring
   * Each computer is connected in a ring to each other.
   
   * Only one computer has command of network resources at a time. This is called "having the token".
   
   * The network sends a "token" throughout the ring, which contains identitiy of the computer allowed to use the network.
   All other computers must wait to use the network.
   
   * No possiblity of collisions.
   
 * Ethernet
   * Multiple computers connect to a single hub or switch.
   
   * Hub
     * Broadcasts the data to all the computers
     
   * Switch
     * Sends data to a specific computer
   
   * The more computers you add to an ethernet network the greater the chance of collisions.
   
   
# 12/22/16
#Aim: Cisco in an hour™	III: In 3-D!

  <b>Data Link Layer</b>
  
  * Point-to-point transmission between devices on the same local network.
  
  * Ethernet Connections:
  
    * Each device is given a unique 6-Byte MAC (Media Access Control) address, this is set on each network card when it is made.
    
    * Data is packaged into frames
    
      * Ethernet Frame:
        * \<prefix\>\<dest\>\<...\>\<data\>\<checksum\>
        *  8B, 6B, 6B, 6B, 46-1500B, 4B
        
        * prefix: 10101010 x7 + 10101011
        * destination/source: MAC addresses
        * ...: Information about frame type
        * checksum: to ensure data integrity
        
      * MTU
        * Maximum Transmission Unit
        
        * 1500 Bytes for ethernet

# 1/3/17
#Aim: Cisco in an hour™	IV: A New Hope

  <b>Network Layer</b>
  
  * Transmission of data between two separate networks
  
  * Is not concerned with whether or not data was sent successfully (connectionless).
  
  * Major features of this layer are addressing, routing and packet forwarding.
  
  * IP (internet protocol) address
  
  * IPv4: 4 byte address
  
    * [0-255].[0-255].[0-255].[0-255]
  
  * Routing is made easier by having IP addresses distributed in blocks.
    
    
# 1/4/17
#Aim: Cisco in an hour™ V for Vendetta

  <b>Network Layer, cont.</b>
  
    * Data is broken into packets (IPv4)
  
      * \<header info\>\<packet length\>\<fragment info\>\<time-to-live\>\<protocol\>
    
      * 2B, 2B, 4B, 1B, 1B
    
      * \<header checksum\>\<source\>\<destination\>\<...\>\<data\>
    
      * 2B, 4B, 4B, 4B, 20-65,535B
    
        * header info: packet type (IPv4/6), header length...
      
        * fragment info: full payloads may be broken up, this will have a total # of fragments, which fragment...
      
        * time-to-live: maximum number of hops before the packet dies
      
        * protocol: TCP/UDP/...
      
        * ...: optional information depending on protocol, type etc.
      
    * IPv4 MTU (max transmission unit) is 65,535 B
    
  * IPv6
    
    * Biggest difference is the address space gors from 2^32 --> 2^128
    
    * Addresses are written as 8 groups of 4 hexadecimal digits (leading zeroes are ignored)
    
    * Jumbograms: Increases the MTU to ~4.3 billion (2^32)
    
    * Other improvements in IPv6 make the protocol incompatible with IPv4.
    
    
    
    
