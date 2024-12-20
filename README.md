# Simple_MPI_Parallel_Computing_Program
**Implementation of MPI Programs for Parallel Computing**

---

## Objective

This repository contains implementation of MPI-based parallel computing programs. The experiment focuses on exploring MPI concepts such as broadcasting, parallel summation, and distributed computation of Mandelbrot sets. The repository demonstrates how to leverage MPI for efficient parallel processing.

---

## Features

- **Broadcasting Arrays:**:  
  Measure wall clock time for broadcasting an array of doubles across multiple processes.

- **Parallel Summation**:  
  Adjust summation programs to work for p processors where the array size is divisible by p.

- **Custom Communication Using MPI_Send/Recv**:  
  Implement summation using MPI_Send and MPI_Recv instead of MPI_Scatter and MPI_Gather.

- **Squaring Numbers in Parallel**:  
  Distribute and square numbers using MPI_Scatter and MPI_Gather.

- **Mandelbrot Set Computation**:  
  Generate a Mandelbrot set visualization using parallel computation.

---

## How To Run

### **Broadcasting Array Program**
After setting up the cluster with 3 virtual machines and 1 NFS server. This program uses MPI (Message Passing Interface) to demonstrate parallel broadcasting of an array of doubles from one root process to all other processes. For this program root process (rank 0) broadcast array of doubles to all other processes in a distributed environment. 

We can run program by using command below:

```bash
[cc@2074557-3 Assignment2]$ /usr/lib64/mpich/bin/mpirun -n 4 -f host_file ./broadcast_doubles
Defining 4 doubles ...
Node 2 writes 4 doubles:
Node 1 writes 4 doubles:
0.000000
0.000000
Node 3 writes 4 doubles:
1.000000
1.000000
0.000000
2.000000
2.000000
1.000000
3.000000
3.000000
2.000000
3.000000
Time taken to broadcast array of 4 doubles: 0.000065 seconds
```
---


