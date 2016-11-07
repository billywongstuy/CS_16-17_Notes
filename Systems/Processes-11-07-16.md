#Aim: Are your proccesses running? - Then you should go out and catch them!

##Processes

  Every running program is a process. A process can create subprocesses, but these are no 
  different from regular processes.
  
  A processor can handle 1 process per cycle (per core). "Multitasking" appears to happen because
  the processor switches between all the active processes quickly.
  
  pid
  
    Every process has a unique identifier called the pid.
    
    pid 1 is the init process
    
    Each entry in the /proc directory is a current pid
    
  getpid() - \<unistd.h\>
  
    returns the current process' pid
    
  getppid() - \<unistd.h\>
  
    returns trhe current process' parent pid
    
##Signals

  Limited ways of sending information to a process.
  
  kill
  
    Command line utility to send a signal to a process
    
    $ kill <PID>
    
      Sends signal 15 (SIGTERM) to PID
    
    $ kill -<no> <PID>
      
      Sends signal <no> to PID
      
    Some commonly used signals: 
      
      1 HUP (hang up)
    
      2 INT (interrupt)
      
      3 QUIT (quit)
      
      6 ABRT (abort)
      
      9 KILL (non-catchable, non-ignorable kill)
      
    killall [-\<SIGNAL\>] \<PROCESS\>
    
      Sends SIGTERM (or SIGNAL if provided) to all processes with PROCESS as the name
      
  Signal handling in c programs - \<signal.h\>
  
    kill
      
      kill (\<PID\>, \<SIGNAL\>);
      
      Returns 0 on sucess or -1 (errno on failure)
    
  
##Code  
  ```c
  //standard headers
  #include <signal.h>
  
  static void sighandler(int signo) {
    if (signo == SIGINT) {
      printf ("Nice try!\n");
    }
  }
  
  
  int main() {
    signal(SIGINT, sighandler);
  
    while (1) {
      printf("hello, I'm : %d", getpid());
    }
    
    return 0;
  }
  
  ```
