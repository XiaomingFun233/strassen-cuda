# Strassen-cuda(with performance)

Matrix multiplication CUDA program using Straasen's algorithm

Base on paiweilai'work,Simplified and Test code performance

Test on Tesla T4 ,use Nsight system 2020.3.2v and run on ubuntu18.04

## Instructions for use

Run the following command to compile:

`nvcc -lcublas strass.cu -o strass`

After generating the executable file strass, run it with the following commands and parameters

```linux
./strass 10 100 1000 2
```

10——the number of rows of the A matrix

100——the number of columns of the B matrix

1000—— the number of columns of the A matrix or the number of rows of the B matrix

2 ——Number of times the matrix is sliced/recursed

## Performance

![Efficiency](E:\cuda_code\pro\Efficiency.png)

This operational efficiency includes the CPU execution activity time

![kernel](E:\cuda_code\pro\kernel.png)

This image only shows how efficient the kernel performs

**Due to some problems, the memory usage of the device is not counted in the data, if you are interested, you can check the data report in the test report folder to analyze and judge by yourself**

## Analysis

Theoretically, writing multiplication programs based on strassen's method using recursive methods on GPUs is actually a time-consuming and ineffective task

One reason is that the latency introduced by memory operations on the GPU is actually more than a dozen times that of computing operations. At the same time, recursive operations exacerbate the impact of this problem. I was going to use caching methods such as shared memory to improve this problem, but the actual operation was not ideal, or even worse in performance, so I gave up further attempts in this area.

In conclusion, matrix multiplication using the recursively implemented strassen method is not a good idea on GPUs, and actually introduces a very large memory consumption and operation latency, when I run the performance test with parameters 

```
1000 1000 1000 1 1 8
```

The program has not responded for a long time, which I think has lost value in a practical sense and abandoned further recursive testing

## Acknowledgment

Xingru Chen xingrucz@gmail.com :Provide me with the opportunity to use test equipment and servers

## Note

If you have any questions or copyright issues, please contact me by email

xiaomingchinafun@gmail.com