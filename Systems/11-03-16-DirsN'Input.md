# Aim: Input? fgets about it!

## getcwd - \<unistd.h\>

  Get the current working directory (cwd) of a program
  
  getcwd ( \<STRINGBUFFER\>, \<SIZE\> )
  
    Copies the path of the cwd into the buffer argument (char *)
    
    Copies at most SIZE characters of the path.
    
    
    
## chdir - \<unistd.h\>

  Change the working directory of a program
  
  chdir( \<PATH\> )
  
  Returns 0 if successful, -1 (errno) if not.
  
  Keep track of file paths when using chdir!
  
  

## Command Line Arguments:

  int main (int argc, char *argv[])
  
  program name is considered the first command line argument
  
  argc: number of command line arguments
  
  argv: array of command line arguments   (index 0 is the name of the executable)
 
 
 
## scanf - \<stdio.h\>

  scanf( \<FORMATSTRING\>, \<VAR1\>, \<VAR2\> ...)
  
  Reads in data from stdin using the format string to determine types.
  
  Puts the data in each variable.
  
  Variables must be pointers
  
```c

//DON'T USE SCANF FOR STRINGS!!!!!!!!!!!!!!!

int x; float f; double d;
printf("\nenter data: ");
scanf("%d %f %lf", &x, &f, &d);
printf("%d %f %lf \n",x,f,d);

```



  
  
