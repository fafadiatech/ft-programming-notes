# CPython Internals based on [YouTube series](https://www.youtube.com/watch?v=LhadeL7_EIU&list=PLzV58Zm8FuBL6OAv1Yu6AwXZrnsFbbR0S)

1. Compiler converts from code in one format to code in another format
1. Python has a simple Compile stage that generates Byte Code
1. Byte Code is then feeded to Interpreter {from Interpreter comes output}
1. This video series will work on Intepreter step, Compiler is pretty standard setup
1. There are two main directories that we're interested in
    1. `Include`: this is where all the header files are
    1. `Objects`: this is where all the object {.c } files are writtern {implementations of .h files}
1. Other directories:
    1. `Python`: This contains main runtime implementation of Python
    1. `Modules`: This contains all implementation of library modules
    1. `Library`: This contains implementation of standard library modules
    1. `Include/opcode.h`: Contains reference of operations in Python
    1. `Python/ceval.c` contains the main interpreter loop. Interpreters are nothing but a giant `while` loop. viz: `for (;;){}`