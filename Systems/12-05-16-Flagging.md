#Aim: How do we flag down a resource?

Semaphores (created by Edsger Dijkstra)

  IPC construct used to control access to a shared resource (like a file or shared memory).
    
  Essentially, a semaphore is a counter that represents how many processes can
  a resource at any given time.
  
      If a semaphore has a value of 3, then it can have 3 active users.    
    
      If a semaphore has a value of 0, then it is unavailable.
    
    
  Most semaphore operations are "atomic" meaning that they will not be split up into multiple processor instructions.
    
  Semaphore operations:
    Create, 
    set up initial value, 
  up(s)/v(s)
  Release the semaphore to signal you are done with its associated 
  down / p.  
  attempt to take the semaphore 
  
  if the semaphore is 0, wait for it to be available.   
  
  remove a semaphore 
  
  
  Semaphores in C - sys/types.h, sys/ipc.h, sys/sem.h
  
  semget   create/get access to a semaphore 
  
  returns 
  semaphore descriptor or -1
  semget (key, amount,flags)
  key (identifier - use ftok)
  Amount (set of how many)
  flags (permissions)
   Bitwise or IPC_CREAT, IPC_EXCL
  
  
  
