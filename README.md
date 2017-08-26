# xv6-Extension
## Description
  Implement support for threads in xv6.
* Implement a new system call clone() that operates similarly to how fork() does, but does not replicate the memory content. Instead, the child thread's page table has the same mappings as its
parent.
* Write a small library with a similar interface to pthread, that allows for basic thread creation and synchronization.
* Add support for locks, involving the required support from the hardware (assembly code), operating system, and thread library.

## Authors
*	Sikai Ni
*	Xuan Fei
## Functions
*	int clone(void (*fcn)(void*), void *arg, void *stack)  

    Create clone function, where we produce a new process which shares the same memory space, the table of file descriptor and the table of signal handler with its parent. The fcn argument is a pointer to a function that is called by the child process. The arg argument is passed to the fcn function. The stack assigns the child process stack.
*	int join(int pid, void**stack)   

    The join function makes the parent process wait for the specific child process. The pid is the process which we are waiting for. The stack is a void stack.
*	int thread_create(struct thread_t *p, void (*fcn)(void*), void *arg)  

    The thread_create function starts a new thread. The fcn is the function executed by the new thread. The arg is passed to the new thread.
*	int thread_join(struct thread_t p)  

    The thread_join function waits for the specified thread to end.
*	void lock_init(volatile lock_t *lock)  

    void lock_acquire(volatile lock_t *lock)  
  
    void lock_release(volatile lock_t *lock)  
  
    The series of function related to lock, which protect the shared resource from being modified by two thread simultaneously.
