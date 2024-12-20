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


---

## How To Run

### **Broadcasting Array Program**
After setting up the cluster with 3 virtual machines and 1 NFS server, this program uses MPI (Message Passing Interface) to demonstrate parallel broadcasting of an array of doubles from one root process to all other processes. For this program root process (rank 0) broadcast array of doubles to all other processes in a distributed environment. 

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
The program ran with 4 processes across the nodes specified in the host_file. Each process printed its received array, confirming successful broadcasting.

### **Parallel Summation Program**
The program divides an array of integers into chunks, distributes these chunks among multiple MPI processes, computes the sum of each chunk locally, and finally aggregates the partial sums at the root process to compute the total sum.

```bash
[cc@2074557-3 Assignment2]$ /usr/lib64/mpich/bin/mpirun -n 4 -f host_file ./parallel_sum_new
Enter the value of n (must be divisible by 4): 8
The data to sum:  1 2 3 4 5 6 7 8
Node 2 has numbers to sum:Node 0 has numbers to sum: 1 2
Node 1 has numbers to sum: 5Node 3 has numbers to sum: 3 6 7 4
 8
Node 2 computes the sum 11

Node 1 computes the sum 7
Node 0 computes the sum 3
Node 3 computes the sum 15
The partial sums: 3 + 7 + 11 + 15 = 36, which should be 36.
[cc@2074557-3 Assignment2]$ 
```
The program takes n = 8 and splits the array [1, 2, 3, 4, 5, 6, 7, 8] among 4 processes. Process 0 computes the sum of [1, 2] as 3. Process 1 computes the sum of [3, 4] as 7. Process 2 computes the sum of [5, 6] as 11. Process 3 computes the sum of [7, 8] as 15. MPI_Scatter divides the array into chunks and distributes them automatically. MPI_Gather collects the partial sums back to the root process. The total sum is computed as 3 + 7 + 11 + 15 = 36. MPI_Scatter simplifies workload distribution and enables parallel computation efficiently.

---


