# Collatz Conjecture
The Collatz conjecture is one of the most famous unsolved problems in mathematics. The conjecture asks whether repeating two simple arithmetic operations will eventually transform every positive integer into 1.
## Problem Statement
The Collatz conjecture concerns what happens when we take any positive integer n and apply the following algorithm:  
n = { n∕2, if n is even  
      3 × n + 1, if n is odd  
The conjecture states that when this algorithm is continually applied,
all positive integers will eventually reach 1.  
For example, if n = 35, the sequence is
35, 106, 53, 160, 80, 40, 20, 10, 5, 16, 8, 4, 2, 1  
Write a C program using the fork() system call that generates this
sequence in the child process. The starting number will be provided
from the command line. For example, if 8 is passed as a parameter on
the command line, the child process will output 8, 4, 2, 1. Because the
parent and child processes have their own copies of the data, it will be
necessary for the child to output the sequence. Have the parent invoke
the wait() call to wait for the child process to complete before exiting
the program. Perform necessary error checking to ensure that a positive
integer is passed on the command line.

## Getting Started
Need to have a Linux based OS.
### Install Components
```
sudo apt-get update
sudo apt-get upgrade  
sudo apt install build-essential
```
### Running the Program
Make sure your terminal is open in the directory where Collatz_Conjecture.c file is  
```
gcc Collatz_Conjecture.c -o Collatz_Conjecture
./Collatz_Conjecture
```
## Important System Calls used in the Program
### fork()
Fork system call is used for creating a new process, which is called child process, which runs concurrently with the process that makes the fork() call (parent process). 
It takes no parameters and returns an integer value.  
Different return types of fork() are
1)	Positive value- returned to parent, and the value is the  process id of the newly created child process.
2)	Zero- return to the child process.
3)	Negative – child process creation was not successful  
  
Lets see what happens when 2 fork() calls are called to get a better understanding  
<pre>
fork ();   // Line 1
fork ();   // Line 2

       P1       // There will be 1 child process 
    /     \     // created by line 1.
  P1      P2    // There will be 2 child processes
 /  \    /  \   //  created by line 2
P1  P3  P2  P4  // There will be 4 child processes 
</pre>
### wait()
A call to wait() blocks the calling process until one of its child processes exits or a signal is received. After child process terminates, parent continues its execution after wait system call instruction.  
  
![s (1)](https://user-images.githubusercontent.com/58753266/200109353-c448023d-1f51-4d66-9c36-39b41ec6650b.jpg)

#### Syntax
```
pid_t wait(int *stat_loc);  
```
Takes one argument status and returns a process ID of dead children or returns -1 immediatly if the process has no child process.  

## Working of the program
<ul>
<li>The program first asks the user to enter a number to run the Collatz Conjecture.</li>
<li> Then <code>fork()</code> is called and the child process is created.</li>
<li><code>if(pid==0)</code> only allows the child process to run the code inside if statement. So child process runs the Collatz Conjecture. </li>
<li>The parent process will be waiting for the child process to finish its execution because of the <code>wait(NULL)</code> statement.</li>
<li>Then parent process will also be terminated.</li>
</ul>

## Sample Output of the Program  
![image](https://user-images.githubusercontent.com/58753266/200119413-01a17525-5604-4b12-8625-305c24a3c014.png)
