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
1. `make -j4` allows you to build source code in parallel using multi-cores {4 is number of core we would like to use}. `-jall ` can be used for optimizing compilation step {gcc flag}
1. `compile(open(source_file).read(), file_name_for_error_processing, mode)` will convert source file to `code object` {which contains byte code}
1. `co_code` from code object returns a byte script
1. `[byte for byte in c.co_code]` will print out the code. `[ord(byte) for byte in c.co_code]` which will output human readable integer
1.  `python -m dis test.py` will show output of byte code dis-assemebled. 
    - First column: Line Number
    - Middle column: Opcode
    - Last column: Optional Arguments
1. All byte-code definitions are mapped in `Include/opcode.h` as constants defined as `# define ..` statements. All Byte code after `HAVE_ARGUMENT` take argument, all those above it don't take an argument
1. All python modules like `dis.py` etc are stored in `Lib` directory. To understand more about how the code object works in Python `dis.py` has all the details
1. [byteplay](https://code.google.com/archive/p/byteplay/) is a nicer bytecode disassember alternative to `dis.py` 
1. Python virtual machine is [stack machine](https://en.wikipedia.org/wiki/Stack_machine)
1. Value stack is used to store constants {Stack which grows down}
1. `STORE_NAME` will pop from Value stack and allocate it to memory
1. `LOAD_NAME` opcode will load value for item and push onto stack
1. Python interpreter uses reference counting, this is how garbage collection is done
1. `PyEval_EvalFrameEx` this is the main interpreter loop
    1. `PyObject **stack_pointer` is value stack. `**` is an array of pointers
    1. `TSC` stands for [time stamp counter](https://en.wikipedia.org/wiki/Time_Stamp_Counter)
    1. Macros: Which are short hand {Two kind of these}
        1. `#define`, left is replace by right side
        1. ...
    1. `switch(opcode)` is one of the key things in Interpreter
1. Everything in Python is an object `PyObject`
1. [dis](https://docs.python.org/2/library/dis.html) has more details on how each of the opcode works
1. Generally each opcode takes 1 byte and 1 byte for argument. `BINARY_ADD` is 1 byte, since it doesn't have any arguments