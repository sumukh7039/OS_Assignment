# A multithreaded program that outputs prime numbers

## Problem Statement

Write a multithreaded program that outputs prime numbers. This program should work as follows: The user will run the program and will
enter a number on the command line. The program will then create a
separate thread that outputs all the prime numbers less than or equal to
the number entered by the user.

## Running the Program

Make sure your terminal is open in the directory where FindPrime.c file is

```
gcc FindPrime.c -o FindPrime
./FindPrime
```

## Important Functions and Data types used in the Program

### pthread_t :

pthread_t is the data type used to uniquely identify a thread. It is used by the application in function calls that require a thread identifier.

### pthread_create() :

It is used to create new thread.<br>
Syntax:

```
int pthread_create(pthread_t * thread,
                   const pthread_attr_t * attr,
                   void * (*start_routine)(void *),
                   void *arg);
```

Parameters:

- thread: pointer to an unsigned integer value that returns the thread id of the thread created.
- attr: pointer to a structure that is used to define thread attributes like detached state, scheduling policy, stack address, etc. Set to NULL for default thread attributes.
- start_routine: pointer to a subroutine that is executed by the thread. The return type and parameter type of the subroutine must be of type void \*. The function has a single attribute but if multiple values need to be passed to the function, a struct must be used.
- arg: pointer to void that contains the arguments to the function defined in the earlier argument

`pthread_create()` returns zero when the call completes successfully. Any other return value indicates that an error occurred.

### pthread_join():

It is used to wait for the termination of a thread.
Syntax:

```
int pthread_join(pthread_t th,
                 void **thread_return);
```

Parameter:

- th: thread id of the thread for which the current thread waits.
- thread_return: It is the location where the exit status of the joined thread is stored. This can be set to NULL if the exit status is not required.

pthread_join() returns zero when it completes successfully. Any other return value indicates that an error occurred.

## Working of the program

- The program first asks the user to enter a number.
- Then a new variable th1 is created of data type pthread_t.
- A thread is created and it is made to run `void *thread1(void *arg)`.
- Because of `pthread_join(th1, NULL);` we wait till thread1 has completely executed.

## Sample Output of the Program
