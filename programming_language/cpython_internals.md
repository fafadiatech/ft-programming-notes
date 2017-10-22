# CPython Internals based on [YouTube series](https://www.youtube.com/watch?v=LhadeL7_EIU&list=PLzV58Zm8FuBL6OAv1Yu6AwXZrnsFbbR0S)

This series cover CPython backend

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
1. Python object protocol are list of methods that all Python objects implement

# From Source to Code: How CPython's Compiler Works based on [YouTube](https://www.youtube.com/watch?v=R31NRWgoIWM)

This talk is complementary to above series in a sense it talks about CPython's Frontend

1. [Design of CPython’s Compiler](https://docs.python.org/devguide/compiler.html) talks about compiler design from Source to Byte Code 
1. Flow of a typical Python code:
    1. Decoding
    1. Tokenizing
    1. Parsing
    1. AST
    1. Compiling
1. `echo "x=3+4" | python -m tokenize` tokenizes a python statement
1. Modules that help tokenize `keyword` and `tokenize`
1. Grammer for Python resides in `Grammar/Grammar` which is written in [EBNF form](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_form)
1. Python uses [LL(1)](https://en.wikipedia.org/wiki/LL_parser)
1. Modules that help `parser`, `symbol` and `token`
1. `AST` {Abstract Syntax Tree} was introduced in Python 2.6 its in `ast` module
1. `Peepholer` is byte code optimizer always used. Reference [Peephole Optimization](https://en.wikipedia.org/wiki/Peephole_optimization)
1. `compile`, `dis` and `symtable` are modules that help in compiliation step

# Stepping Through CPython based on [YouTube](https://www.youtube.com/watch?v=XGF3Qu4dUqk)

1. `Misc` contains misc code
1. `PC` and `PCbuild` contain code for building Python on Windows
1. `Doc` contains documentation
1. Structure of the code
    1. `Include` contains public facing headers. This get installed when you install Python
    1. `Lib` contains all .py files which are implementation of standard library
    1. `Modules` contain C portion of Python standard library implementation
    1. `Objects` where objects are implemented List, Dictionary, Set and Tuples
    1. `Python` this is where interpreter, parser etc reside
1. Main lives in `Modules/python.c` -> now renamed to `Modules/main.c` which ultimately calls `Py_Main`
1. There are two families of Memory Management in Python {malloc, realloc and free}
    1. PyMem_:
        - These live in `Include/pymem.h` and `Objects/object.c`
        - These are thin wrapper over offical `malloc` function
    1. PyObject_memory
        - Lives in `Include/objimpl.h` and `Objects/obmalloc.c` will be enable if `#define WITH_PYMALLC` is turned on
        - `PyObject_Malloc` custom small block allocator
1. Py_Main
    1. Parses argument
    1. Checks Environmental Varaibles
    1. Intializes Standard Input and Output
    1. `Py_Initialze` bootstraping
    1. run script/function
1. Everything in Python is `PyObject` {If Python were implemented in C++ this is where all objects would inherit from}
    1. Resides in `Include/object.h` and `Objects/object.c`
        - This is where `ob_refcnt` which is object's reference count is stored
1. `PyTypeObject` 52 members atleast
    - Some are function pointers
1. Protocol is another name for Abstract Base class `Include/abstract.h` and `Objects/abstract.c`. There are 5 protocol
    - Object
    - Buffer `tp_as_buffer` {struct needs to added}
    - Number `tp_as_number`
    - Mapping `tp_as_mapping`
    - Sequence `tp_as_sequence`
1. Reference Counting
    - `Py_INCREF`
    - `Py_DECREF`
    - `Py_XINCREF` {safe versions checks NULL before incrementing}
    - `Py_XDECREF`
    - `Py_CLEAR`
1. `PyObject_` has linked list of arena objects {which are blocks of 256K} memory. Each have 4K blocks. Each 4K block has {Each 4K blocks are called pool}
    - `struct pool_header` how big and free list pointer
1. Circular Double Linked List for `struct pool_header` {for things that are partially in used}
1. `PyEval_EvalFrameEx` lives in `Python/ceval.c` implements stack-based virtual machine
1. There are python modules that are pre-loaded {as part of bootstraping}
1. 