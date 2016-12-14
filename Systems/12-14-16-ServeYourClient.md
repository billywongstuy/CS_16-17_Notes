#Aim: Always remember to tip your servers

##Server/Client Program Paradigms

  * Handshake
  
    * A procedure to ensure that a connection has been established.
    
    * Both ends of the connection must verify that they can send and receive data to and from each other. 
    
      * Basic Handshake Procedure:
      
        1. Server creates a FIFO (Well Known Pipe)
        
        2. Server waits for a connection
        
        3. Client creates a "private" FIFO
        
        4. Client connects to server and sends the private FIFO name
        
        5. Client waits for a message from the server
        
        6. Server receives client's message and removes the WKP
        
        7. Server connects to client FIFO, sending an initial acknowledgment message.
        
        8. Client receives server's message, removes its private FIFO
        
        9. Client sends message back to server
