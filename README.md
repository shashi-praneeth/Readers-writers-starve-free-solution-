# Readers-writers-starve-free-solution-`

For solving starve free readers writers problem we assign the critical section to whom first arrives among reader and writer. The writer waits till all the readers and writers who all arrived before it are completed. Where as succesive Readers can access critical section all at once.

We need a semaphore that take care of processes in a First-In-First-Out order and another semaphore to increase the th readers count . another semaphore for mutual exclusion of reader and writer .

```c++
FOR WRITER'S

  Wait(FCFS);
  wait(wrt);
  
 // Critical section //
 
  Signal(wrt);
  Signal(FCFS); 
  
```

```c++
  
  
FOR READER'S 
  
  Wait(FCFS);
  
  Wait(mutex);
  
  readercount++;
  if (readercount==1){
    wait(wrt);
  }
  
  Signal(mutex);
  
  Signal(FCFS);
  
 //Critical section //
 
  Wait(mutex);
  
  readercount--;
  if (readercount==0){
  Signal wrt;
  }
  
  Signal(mutex); 

```
int readercount (initially eqaul to 0).

semaphore mutex .(intially eual to 1)

semaphore FCFS . (initially equal to 1)

semaphore wrt . (intitially equal to 1)

Multiple readers can simultaneously read the resource.
When a writer is updating wrt semaphore is locked. And also ensures no new process can begin reading by using the FCFS semaphore. Hence writers do not starve in this scheme.

