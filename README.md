# High-Performance Tiled GEMM in CUDA

This repository contains a custom, highly optimized General Matrix Multiply (GEMM) kernel written in C++/CUDA. It was developed to explore GPU memory hierarchy and parallel performance optimization techniques, specifically comparing a naive global-memory implementation against a shared-memory tiled approach.

##  Features & Optimizations
* **2D Shared-Memory Tiling:** Maximizes L1 cache/shared memory reuse to drastically reduce global memory bandwidth bottlenecks.
* **Memory Coalescing:** Eliminates uncoalesced global memory transactions during tile loads.
* **Robust Validation:** Includes strict floating-point validation comparing kernel outputs to a CPU baseline using both absolute and relative error tolerances.
* **Hardware Profiling:** Designed to be profiled with NVIDIA Nsight Compute to analyze warp occupancy and memory throughput.

##  Performance Benchmarks
Tested on large dense matrices ($2048 \times 2048 \times 2048$).

| Implementation | Execution Time | Throughput | Speedup |
| :--- | :--- | :--- | :--- |
| **Naive GEMM** | 31.44 ms | 546.34 GFLOPS | Baseline |
| **Tiled GEMM** | 24.10 ms | 712.59 GFLOPS | **1.30x** |

*Note: Validation passed with 0 mismatches across all matrix elements.*

