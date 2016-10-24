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

```c
  #include <stdio.h>
  #include <stdlib.h>
  #include <fcntl.h>

  int fd;
  fd = open("tester",0_RDONLY);
  printf("fd: %d\n", fd);
  printf("error: %d - %s\n",errno,strerror(errno));
  
  close(fd);
```




read (int fileDescriptor, void * buff, int bytecount)

Copies up to bytecounts bytes from fileDescriptor into buffer starting from buff

returns amount of bytes read


write (int fileDescriptor, const void *buff, int bytecount)

writes up to bytecounts bytes from buff to fileDescriptor

returns amount of bytes written
