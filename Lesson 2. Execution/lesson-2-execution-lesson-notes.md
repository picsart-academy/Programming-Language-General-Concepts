# Lesson 2. Execution

Language types by compilation and execution
- Compiled
- Interpreted
- Hybrid

Times
- The compile time
- The run time

## Virtual machines

Types of virtual machines
- Full instruction set architecture (ISA) virtual machine provides full computer system's ISA emulation or virtualization. Guest operating system and applications can run on the top of the virtual machine as on an actual computer (VirtualBox).
- Application Binary Interface (ABI) virtual machine provides a guest process ABI emulation. Applications against that ABI can run in the process side by side with other processes of native ABI applications (Intel's IA-32 Execution Layer on Itanium).
- Virtual ISA virtual machine provides a runtime engine so that applications coded in the virtual ISA can execute on it. Virtual ISA usually defines a high-level and limited scope of ISA semantics, so it does not require the virtual machine to emulate a full computer system (JVM, CLR).
- Language virtual machine provides a runtime engine that executes programs express in a guest language. The programs are usually presented to the virtual machine in source form of the guest language, without being fully compiled into machine code beforehand. The runtime engine needs to interpret or translate the program and also fulfill certain functionalities that are abstracted by the language such as memory management (Lisp, Tcl, Ruby).

The boundaries between virtual machine types are not clear-cut. The first two are sometimes called emulators.

Why virtual machines?
- Cross-platform execution
- Memory safety
- Operation safety
- Control safety

Components of VM
- loader and dynamic linker, metadata generation
- execution engine
- memory manager (vm data, app data)
- thread scheduling
- resource manager

