#Aim: How do we flag down a resource?

  Semaphores (created by Edsger Dijkstra)

  IPC construct used to control access to a shared resource (like a file or shared memory).
    
  Essentially, a semaphore is a counter that represents how many processes cana resource at any given time.
  
    If a semaphore has a value of 3, then it can have 3 active users.    
    
    If a semaphore has a value of 0, then it is unavailable.
    
  Most semaphore operations are "atomic" meaning that they will not be split up into multiple processor instructions.
    
  Semaphore operations:
  
    Create a semaphore
    
    Set up initial value
    
    up(s)/v(s)
      Release the semaphore to signal you are done with its associated 
    
    down / p(s)
      attempt to take the semaphore 
      
      if the semaphore is 0, wait for it to be available.   
    
    remove a semaphore 
  
  
  Semaphores in C - sys/types.h, sys/ipc.h, sys/sem.h
  
    semget   
      
      create/get access to a semaphore 
    
      returns semaphore descriptor or -1
      
      semget (key, amount,flags)
      
        key (identifier - use ftok)
        
        amount (set of how many)
        
        flags (permissions)
          Bitwise or IPC_CREAT, IPC_EXCL
   
   
#Aim: What\'s a semaphore? - To control resources

  Semaphore code
  
  semctl - sys/types.h , ...

    Control the semaphore including:
   
      Set the semaphore value

      Remove the semaphore

      Get the current value
 
      Get information about the semaphore

    These operations are not atomic

    semctl (DESCRIPTOR, INDEX, OPERATION, DATA)
    
      DESCRIPTOR: return value of semget
    
      INDEX: index of semaphore you want to control in DESCRIPTOR (for single semaphore set 0)
      
      OPERATION: One of the following (IPC_RMID: remove semaphore, SETVAL: set value [requires DATA], SETALL: set value for every semaphore in set, GETVAL: return value, IPC_STAT: populate buffer with information about the semaphore)
      
      DATA: 

#Code
```c
union semun {

}


int main (int argc, int *argv[]) {
  int semid;
  int key = ftok("makefile",22);
  int sc;

  if (strcmp( argv[1], "-c", strlen(argv[1])) == 0) {
    semid = semget(key,1,IPC_CREAT | 0644);
    printf("semaphore created: %d\n", semid);
    union semun su;
    su.val = 1;
    sc = semctl(semid,0,SETVAL,su);
    printf("value set: %d\n",sc);
  }
 
  else if (strcmp( argv[1], "-v", strlen(argv[1])) == 0) {
    semid = semget(key,1,0);
    sc = semctl(semid,0,GETVAL);
    printf("semaphore value: %d\n", sc);
  }
  
  else if (strcmp( argv[1], "-r", strlen(argv[1])) == 0) {
    semid = semget(key,1,0);
    sc = semctl(semid, 0, IPC_RMID);
    printf("semaphore removed: %d\n",sc);
  }
}


```
  
  
  
