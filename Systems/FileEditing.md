#Aim: Opening up a world of possiblities

##open - \<fcntl.h\>

  Add a file to the file table and returns its file descriptor
  
  If open fails, -1 is returned, extra error information can be found in errno.
  
  errno is an int variable that can be found in <errno.h>, using strerror (in string.h) on errno will return a string 
  descriptor of the error
  
  ```c
  open(<PATH>,<FLAGS>,<MODE>)
  ```
  
##mode
  
  Only used when creating a file. Set the new file's permissions using a 3 digit octal #
    
  
##flags
  
    Determine what you plan to do with the file.
    
    Use the following constants:
    
    O_RDONLY
    O_WRONLY
    O_RDWR
    O_APPEND
    O_TRUNC
    O_CREAT
    O_EXCL: when combined with O_CREAT, will return an error if the file exists
    
    Each flag is a number, to combine flags use bitwise or
    
    O_WRONLY = 1                  00000001
    O_APPEND = 8                  00001000
    O_WRONLY | O_APPEND  =        00001001
    

#close

  Remove a file from the file table.
  
  Returns 0 if successful. Returns -1 and sets errno if unsuccessful.


#Aim: Read Your Writes!

##umask - \<sys/stat.h\>
  Set the fuke creation permission mask

  By default, created files are not given the exact permissions provided in the mode argument to open. 
  Some permissions are automatically shut off.
  
  Umask is applied by using bitwise negation on the mask, then bitwise and-ing it to the mode
  
    new_permissions = ~mask & mode

  The default mask is 022.
  
  
          0    2      2
          
| mask | 000 | 010 | 010 |
| ---- | :-: | :-: | --: |
| mask | 111 | 101 | 101 |
| mode | 110 | 110 | 110 |
| &    | 110 | 100 | 100 |

  
  reset the mask with umask(000) or umask(0)
  
  
##read

  Read in data from a file
  
  read(<FILEDESCRIPTOR>, <BUFFER>, <AMOUNT>)
  
  read(fd, buff, n) //Read n bytes from the fd's file and put that data into buff
  
  Returns the number of bytes actually read. Returns -1 and sets errno if unsuccessful.
  
  BUFFER must be a pointer.

##write - <unistd.h>

  write data to a file

  write(<FILEDESCRIPTOR>, <BUFFER>, <AMOUNT>)
  
  write(fd, buff, n) //Writes n bytes from buff into fd's file
  
  Returns the number of bytes actually written. Returns -1 and sets errno if unsuccessful.
  
  BUFFER must be a pointer.
  
```c
  #include <stdio.h>
  #include <stdlib.h>
  #include <fcntl.h>

  umask(000);
  int fd;
  fd = open("tester",O_CREAT,0666);
  printf("fd: %d\n", fd);
  printf("error: %d - %s\n",errno,strerror(errno));
  
  close(fd);
```
