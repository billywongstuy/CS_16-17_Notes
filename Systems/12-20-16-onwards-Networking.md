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
    
    
# 1/5/17
#Aim: Cisco in an hour™ VI: The Undiscovered Country

  <b>Transport Layer</b>
  
  * Computer to computer connection over a network
  
  * Unconcerned with the individual hops of layer 3 traffic (what do I with the info?)
  
  * Each destination address has multiple ports (65,535 ports)
  
    * Each port corresponds to a particular service
    
    * ports < 1024 are well known, reserved ports
    
    * Regulated by the Internet Assigned Numbers Authority (IANA)
    
  * TCP: Transmission Control Protocol
  
    * Reliable connection, guarantees delivery of data
    
    * Data is considered a continuous stream that arrives in the order it is sent (which may not be true in the network layer)
    
    * Connections are established using a 3-way handshake
    
      * Server "binds" to a port and waits
      
      * 1. Client sends a SYN message to the server
      * 2. Server sends the client a SYN_ACK mesage
      * 3. Client sends an ACK to the server
      
  * UDP: User Diagram Protocol
  
    * Does not require an explicit connection
    
    * Data is sent as discrete diagrams with a set size (as opposed to a continuous stream)
    
    * Datagrams may be droped or received out of order.
    
    * Assumes that any kind of error checking is handled at later level.
    
    
# 1/6/17
#Aim: Cisco in an hour™ VII: Adrian's Revenge

  <b>Remaining Layers</b>
  
  * 5. Session
  * 6. Presentation
  * 7. Application
  
  * These layers are incorporated into the programs that use network connections.
  
  * Session layer represents end-to-end connections in a program (sockets).
  
  * Presentation layer represents how programs package transmitted data.
  
  * Application layer represents the programs that users interact with.
  
  
  * Sockets (sys/socket.h, sys/types.h)
  
    * A socket is a network connection between two programs.
    
    * A socket has 2 ends, each one consisting of an IP Adress/Port pair.
    
    * To use a socket
      * 1. create the socket
      * 2. bind it to ip port and listen
      * 3. accept (server) /connect (client)
      * 4. send/receive (transmit) data
      
    * socket \<sys/socket.h\>
    
      * Creates a socket
      
      * Returns a socket descriptor (int that works like a file descrptor)
      
      * socket ( domain , type , protocol )
      
        * domain: type of address, IPv4, IPv6...   ---    AF_INET: IPv4
        
        * type: tcp/udp    ---     SOCK_STREAM: tcp, SOCK_DGRAM: udp
        
        * protocol: cobination of domain and type settings
          * If set to 0 the OS will set to correct protocol
          
        * example: int sd = socket(AF_INET, SOCK_STREAM,0);
        
    * bind \<sys/socket.h\>
    
      * Binds the socket to an address and port
      
      * Returns 0 (success) or -1 (failure)
      
      * bind ( socket descriptor , address , address length )
      
        * socket descriptor: return value of socket
        
        * address: pointer to a struct sockaddr_in(6)
        
          * sin_family: adress domain (e.g. AF_INET)
          
          * sin_addr: IP address in binary --- sin_addr.s_addr = INADDR_ANY //any incoming connection/local IP address
          
            * inet_aton ( string , address variable ) - \<arpa/inet.h\>
            
              * will convert a string representing an ip address to the correct format and place it in the second parameter
          
          * sin_port 
            
            * htons(int)
            
              * Returns the port in the correct order    ---- big endian: most significant byte first
              
    * listen (server only) - \<sys/socket.h\>
    
      * TCP server will listen to a socket and wait for an incoming connection
      
      * listen ( socket descriptor , queue length )
      
        * socket descriptor: return value of socket
        
        * queue (doesn't work anymore) : number of connections that can wait
        
    * accept (server only) - \<sys/socket.h\>
    
      * Set up a tcp connection
      
      * Handles the required 3-way handshake
      
      * A complete socket has 5 pieces of information, IP address and port # for both the client and 
      server, and protocol (tcp/udp)
      
      * Once a client connection gets past listen(), accept cteayes a new socket
      with the client information added, and returns a descriptor to the new socket
      
      
              
              
            

# 01/10/2017
#Aim: Socket to Me

  * Look at previous lesson starting at sin_addr
    
  * network standard for storing ports: big endian  
  
  
# Code (server)
```c
//headers

int sd;
int connection;
char buffer[200];

sd = socket( AF_INET, SOCK_STREAM, 0);

struct sockaddr_in sock;
sock.sin_family = AF_INET;
sock.sin_port = htons(9001);
sock.sin_addr.s_addr = INADDR_ANY;

bind (sd, (struct sockaddr *)&sock, sizeof(sock));

listen(sd,1);

return 0;

```
    
# Code (client)
```
int sd;
int connection;
char buffer[200];
char *host = "127.0.0.1";

sd = socket( AF_INET, SOCK_STREAM, 0);

struct sockaddr_in sock;
sock.sin_family = AF_INET;
sock.sin_port = htons(9001);
sock.sin_addr.s_addr = INADDR_ANY;

inet_aton(host,&(sock.sin_addr));

 bind (sd, (struct sockaddr *)&sock, sizeof(sock));
 
```
