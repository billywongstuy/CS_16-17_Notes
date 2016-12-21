# 12/20/16
#Aim: Cisco in a hour

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
#Aim: Part II: Electric Boogaloo

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
   
   
        
