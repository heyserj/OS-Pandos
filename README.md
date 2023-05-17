# OS-Pandos
This project implements Pandos, a low-level operating system. Note that this project was part of an upper-level computer science course I took at Xavier during
my senior year. To implement Pandos, I worked with one other individual from class, and, using paired programming, we implemented the first three layers (or
phases) of the OS, which are found in the directories labeled "phase1," "phase2" and "phase3." The header files for the nine corresponding files can be found
in the directory called "h." 

The first phase of Pandos allows for the allocation and deallocation of process control blocks (pcb's), which are identical to processes, as we often refer to
them as. The first phase also implements the maintenance of queues of pcb's, the maintenance of trees of pcb's and the maintenance of a single sorted list of
active semaphore descriptors, each of which supports a queue of pcb's known as the active semaphore list (ASL). In this phase, a semaphore is simply an integer
with a memory address and process queue associated with it. The accompanying file named "p1test.c" will test the data structures implemented in this phase.

The second phase of Pandos builds on the previous phase in two ways. First, this level receives control from the exception handling facility used in the previous
level, so this phase handles some of the more common exceptions that may occur (i.e., TLB-refill events, which occur during address translation when no matching 
entries are found in the TLB, syscall exceptions, interrupts, TLB exceptions and program trap exceptions). Only syscalls 1-8 are implemented in this level;
additional syscalls are implemented in phase three. This phase also implements a scheduler for running the pcb's that are ready to be executed. (These pcb's are 
stored in this phase's "ready queue.") Note that the scheduler in this phase enables Pandos (and the associated code included in this repository) to support 
multiprogramming. Furthermore, note that this phase implements the main() function, which is the entry point for Pandos. Thus, all global variables for Pandos 
are also declared and initialized in this level.

The third phase of Pandos (and the last phase that I implemented) adds on the previous two layers because it creates an environment for the execution of user
processes (called U-proc's). To do so, this phase adds support for address translation/virtual memory, and it also adds support for character-oriented I/O devices
(i.e., terminals and printers). Note that each U-proc is assigned its own printer and terminal. More specifically, phase three also provides exception handling 
for page faults and non-TLB exceptions (i.e., syscall exceptions numbered nine and above, as well as all program trap exceptions). Finally, this level adds a more
in-depth TLB-refill event handler, as one will refrain from using the placeholder TLB-refill event handler that was provided in earlier phases (Goldweber and 
Davoli, 2020).
