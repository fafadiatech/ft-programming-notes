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
1. `HAS_ARG` macros checks if a macro which checks if an Opcode has an argument
1. `Py_DECREF` will decrement the reference count {This the garbage collection stuff}. `Py_INCREF` will increment the reference
1. [Python Tutor](http://pythontutor.com/) is tool for visualizing execution of code step by step
1. [What is the difference between a frame and object, and when should I modify one over the other?](https://stackoverflow.com/questions/40641615/what-is-the-difference-between-a-frame-and-object-and-when-should-i-modify-one)
1. Stack frames are created when a function is **called** rather than when they are defined
1. `Values` are stored in `Stack`, `Functions` are stoed in `Frames`
1. Each function in python gets compiled into `code object` of its own {function object}
1. `LOAD_CONST` will bind function {until runtime}. This allows to change function dynamically {until its called}. This is for dynamic features
1. Difference between code and function objects is that function object contains extra items. This includes:
    1. Context/Enviroment in which it needs to get executed {A function is closure given a context}
1. `Include/code.h` is code object and `Include/frame.h` is frame object {for functions}
1. Code objects are immutable
1. Each frame has a value stack
1. Both Function and Frame Objects have:
    1. Code Object
    1. Enviroment
1. In case of Recursive code we can have 4 Frames and Just 1 Function {E.g. recursive factorial}
1. Frames are runtime represetnation of a function with its own value stack and local variables
1. `CALL_FUNCTION` opcode implements calling of a function 
1. `PyFrame_New` is called withing `fast_function`. So everytime a function is called a new frame is created
1. `f_localplus` is storage for value stack {local one} which get copied over from calling stack