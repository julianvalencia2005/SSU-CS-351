# Project 4

## CUDA iota
This program implements the iota function using CUDA and compares GPU and CPU performance.

## CPU Timing Results
|Vector<br>Length|Wall Clock<br>Time|User Time|System Time|
|:--:|--:|--:|--:|
|10| 0.00| 0.00| 0.00|
|100| 0.00| 0.00| 0.00|
|1000| 0.00| 0.00| 0.00|
|10000| 0.00| 0.00| 0.00|
|100000| 0.00| 0.00| 0.00|
|1000000| 0.00| 0.00| 0.00|
|5000000| 0.02| 0.00| 0.02|
|100000000| 0.58| 0.09| 0.47|
|500000000| 2.94| 0.50| 2.43|
|1000000000| 6.07| 0.97| 5.10|
|5000000000|32.65| 5.67|26.97|

## GPU Timing Results
|Vector<br>Length|Wall Clock<br>Time|User Time|System Time|
|:--:|--:|--:|--:|
|10| 0.34| 0.01| 0.31|
|100| 0.25| 0.00| 0.23|
|1000| 0.25| 0.00| 0.22|
|10000| 0.25| 0.00| 0.22|
|100000| 0.25| 0.01| 0.22|
|1000000| 0.28| 0.01| 0.23|
|5000000| 0.27| 0.01| 0.24|
|100000000| 0.88| 0.16| 0.69|
|500000000| 3.42| 0.72| 2.68|
|1000000000| 6.56| 1.47| 5.06|

## Discussion
The GPU version did not significantly outperform the CPU version for smaller vector sizes because CUDA has overhead from launching kernels and transferring memory between the CPU and GPU. The GPU becomes more useful for very large workloads with more computation.

## Julia Set
This program generates a Julia/Mandelbrot image using CUDA.

![Julia Set](julia.ppm)
