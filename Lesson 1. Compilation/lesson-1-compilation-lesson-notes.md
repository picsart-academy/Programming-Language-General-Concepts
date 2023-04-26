# Lesson 1. Compilation

Source: Compilers. Principles, Techniques, and Tools by Aho, Lam, Sethi, Ullman 

A compiler is a program that can read a program in one language - the source language - and translate it into an equivalent programin in another language - the target language.

Instead of producing a target program as a translation, an interpreter appears to directly execute the operations specified in the source program on inputs supplied by the user.

A source program may be divided into modules stored in separate files. The task of collecting the source program is sometimes entrusted to a separate program, called a preprocessor. The modified source program is then fed to a compiler. The compiler may produce an assembly-language program as its output, because assembly language is easier to produce as output and is easier to debug. The assembly language is then processed by a program called an asssembler that produces relocatable machine code as its output.

Large programs are often compiled in pieces, so the relocatable machine code may have to be linked together with other relocatable object files and library files into the code that actually rns on the machine. The linker resolves external memory addresses, where the code in one file may refer to a location in another file. The loader then puts together all of the executable object files into memory for execution.

The analysis part breaks up the source program into constituent pieces and imposes a grammatical structure on them. The analysis part reports on errors, also collects information about the source program and stores it in a data structure called a symbol table, which is passed along with the intermediate representation to the synthesis part.
The synthesis part constructs the desired target program from the intermediate representation and the information in the symbol table. The analysis part is often called the front end of the compiler; the synthesis part is the back end.

![Compiler Phases](https://raw.githubusercontent.com/picsart-academy/Programming-Language-General-Concepts/main/Lesson%201.%20Compilation/compiler.png)

## Lexical Analysis

The first phase of a compiler is called lexical analysis or scanning. The lexical analyzer reads the stream of characters making up the source program and groups the characters into meaningful sequences called lexemes. For each lexeme, the lexical analyzer produces as output a token of the form `<token-name, attribute-value>`
that it passes on to the subsequent phase, syntax analysis. 

In the token, the first component `token-name` is an abstract smbol that is used during syntax analysis, and the second component `attribute-value` points to an entry in the symbol table for this token. Information from the symbol table entry is needed for semantic analysis and code generation. 

For example, for the following source
```
position = initial + rate * 60
```
we get 
```
<id, 1> <=> <id, 2> <+> <id, 3> <*> <60>
```

where id is an abstract symbol standing for identifier and 1, 2, or 3 points to the symbol table entry for particular identifier.

## Syntax Analysis

The second phase of the compiler is syntax analysis or parsing. The parser uses the first components of the tokens produced by the lexical analyzer to create a tree-like intermediate representation that depicts the grammatical structure of the token stream. A typical representation is a syntax tree in which each interior node represents an operation and the children of the node represent the arguments of the operation.
