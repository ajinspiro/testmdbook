# Introduction

### What is an interpreter ?

Interpreters and compilers are things that are used to instruct a computer how to act according to its user's needs. Differentiating an interpreter from a compiler is less straightforward today because modern implementations of interpreters like JavaScript and Python have a compiler component within them and modern compilers like Java and C# have an interpreter component in their pipeline. 

A simple interpreter is a program that takes a string (source code) as input and performs the actions in that source code one by one. The action can be something like executing a function that prints out the details of weather in Kochi.

A very large portion of developer population have no idea what is going on inside an interpreter. They think interpreters as black boxes that have big nerdy stuff going inside only Einsteins and Curies can understand. This pragmatic guide lets you see inside those black boxes, and understand the intricacies within so that you too can build one when the necessity comes, and it comes way more often than you might think.

The interpreter we are going to build in this book is called ARLang. ARLang will have 4 stages in its interpretation process. You can picturize them forming a pipeline, where one stage's output is the next one's input. 
- Lexical analysis of input string
- Parsing / Generation of Abstract Syntax Tree (AST)
- Semantic Validation of Abstract Syntax Tree (AST)
- AST Traversal and Execution 

These stages can be split into **front end** and **back end**.

Lexical analysis, parsing, and semantic validation together constitute the **front end** of ARLang. Its job begins at reading the source code and ends at producing the AST. This part is mostly platform-independent and generally reusable across platforms.

The **back end** in ARLang is the runtime execution part: it takes the validated AST and performs the program’s behavior which is direct AST evaluation.

So the partitioning criterion for interpreters is:

- **Front end:** “Understand and validate the program.”
- **Back end:** “Execute the program at runtime.”

In more advanced VMs like CPython, the back end may include bytecode generation, bytecode interpretation, and/or JIT compilation, but in a simple interpreter like ARLang, the back end is just AST execution.