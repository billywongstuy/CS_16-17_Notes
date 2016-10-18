##Aim: C, the ultimate hipster, using \# decades before it was cool.

  #

  Used to provide preprocessor instructions
  
  These directives are handled before the compiler really kicks in
  
  ```c
  #include <LIBRARY> | "LIBRARY"
  ```
  -link libraries to your code
  -like a copy and paste (copy LIBRARY functions and paste in file where #include is)
  
  
  ```c
  #define <NAME> <VALUE>
  #define TRUE 1
  ```
  -replace all occurences of NAME with VALUE
  
  
  ```c
  macros:
    #define SQUARE(x) x*x
    ...
    int y = SQUARE(9); //==> int y = 9*9;
  ```
  
  conditional statement:
  ```c
  #ifndef <IDENTIFIER>
  <code>
  #endif
  ```
  -if the identifier has been defined, ignore all the code until the endif statement.
  
  
