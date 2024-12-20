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

### **Broadcasting Array**
After setting up the cluster with 3 virtual machines and 1 NFS server. This program uses MPI (Message Passing Interface) to demonstrate parallel broadcasting of an array of doubles from one root process to all other processes. 
