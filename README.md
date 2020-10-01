# Fix-Race-Condition-using-PThread-Mutex-Locks
The C program stack-ptr.c (provided) contains an implementation of a stack using a linked list. 
An example of its use is as follows:

StackNode *top = NULL; 
... 
push(5, &top); 
push(10, &top); push(15, &top); 
... 
int value = pop(&top); 
value 	= pop(&top); value 	= pop(&top); 

This program had a race condition and was not appropriate for a concurrent environment. Pthreads mutex locks were used to fix the race conditions. 
The now-thread-safe stack was tested by creating 200 concurrent threads in main() that intermix pushing and popping values.

This is how it was tested and ran:

•	Use a loop in main() to create all those threads. Using previous gained knowledge of joining threads.

•	Wrote one testStack function, and used it as the entry point for each thread. 
•	The testStack function intermixes 3 push operations with 3 pop operations in a loop that 
executes 500 times. 
•	All threads used the same stack. 
•	gcc -pthread stack-ptr.c -o stack-ptr is an example command to compile and link 
the program 
