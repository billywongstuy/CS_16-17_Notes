#Aim: How do we flag down a resource?

Semaphores (created by Edsger Dijkstra)

  IPC construct used to control access to a shared resource (
  like a file or shared memory).
  
  
  Essentially, a semaphore is a counter that represents how many processes can
  a resource at any given time.
  
      If a semaphore has a value of 3, then it can have 3 active users.    
    
    
    
 If a semaphore has a value of 0, thr it is unavailable.
    
    
    
