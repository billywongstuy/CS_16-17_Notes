#Aim: Sharing is caring!

##Shared Memory - \<sys/shm.h\>, \<sys/ipc.h\>, \<sys/types.h\>

  A segment of heap memory that can be accessed by multiple processes.
  
  Shared memory is accessed via some key that is known by any process that needs to access it.
  
  Shared memory does not get released when a program exits.
  
  
  
  5 shared memory operations:
  
    Create the segment (happens once)
    Access the segment (happens once per peocess)
    Attach the segement to a variable (once per process)
    Detach the segment from a variable (once per process)
    Remove the segment (happens once)
    
  
  shmget
  
    Create or access a shared memory segment
    
    Returns a shared memory descriptor (similar idea to a file descriptor), or -1 if it fails.
    
    shmget (key, size, flags)
    
      key: Unique integer identifier for the shared memory segment (like a file name).
      
      size: How much memory to request
      
      flags: Includes permissions for the segment
      
        Combine with bitwise or
        
        IPC_CREAT: Create the segment (If it is new, will set value to all 0s)
        
        IPC_EXECL: Fail if the segment already exists and IPC_CREAT is on
    
  shmat
  
    Attach a shared memory segment to a variable
    
    Returns a pointer to the segment or -1 (errno)
    
    shmat(descriptor, address, flags);
    
      descriptor: The return value of shmget
      
      address: If 0, the OS will procide the appropriate address
      
      flags: usually 0, there is one useful flag (SHM_RDONLY: makes the memory read only)
      
      
##Code    
```c
#include <stdio.h>
#include <stdlib.h>
#include <sys/shm.h>
#include <sys/ipc.h>
#include <sys/types.h>


int main() {
  int pid;
  int sd;
  int *a;
  int status;

  sd = shmget(24601, sizeof(int), IPC_CREAT | 0644);
  
  
  pid = fork();
  if (pid == 0) {
    
    a = shmat(sd, 0, 0);
    *a = 37892;
    printf("child: %p\n",a);
    printf("child: %d\n",*a);
    
  }
  else {
    wait(&status);

    a = shmat(sd, 0, 0);
    printf("parent: %p\n",a);
    printf("parent: %d\n",*a);
    
  }
  
}

```
