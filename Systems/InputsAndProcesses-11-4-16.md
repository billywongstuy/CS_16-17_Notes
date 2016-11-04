#Aim: Sending mixed signals

##fgets - \<stdio.h\>

  Read in from a file stream and store it in a string
  
  fgets ( \<DESTINATION\>, \<BYTES\>, \<FILEPOINTER\> )
  
  fgets( s,n,f ): Reads at most n-1 characters from file stream f and stores it in s
  
  File pointer
  
    FILE * type, more complex than a file descriptor
    
    stdin is a FILE * variable
    
  Stops at newline, end of file, or the byte limit.
  
  If applicable, keeps the newline character as part of the string, appends NULL after
   
  
  ```c
  int i; float f; char s[10];
  fgets(s,sizeof(s));
  printf("+%s+\n", s);
  
  
  ```
  
  ps in terminal for all active processes that are attached to a terminal session and originate from you
  
  PIDs are handed out to each process
  
  ps -x show EVERY RUNNING PROCESS
  
  Every process running has a folder in the proc folder
  
  
