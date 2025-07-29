# System Performance Testing with Phoronix Test Suite Benchmarks

The [Phoronix Test Suite](https://openbenchmarking.org/tests) is an open-source benchmarking and comprehensive performance testing tool designed to assess and analyze the performance of hardware systems. It offers a wide range of benchmarks that cover various aspects of system performance, including CPU, GPU, memory, storage, network, file system and many more.  It provides benchmark-specific results such as simulation speed (e.g., ns/day), execution time, or throughput, depending on the test.


Although the Phoronix Test Suite is available as a module on Cheaha, many individual benchmarks require additional dependency installations. To improve the reusability of CPU and GPU benchmarking by the UAB Research Computing (RC) team, the suite has been containerized with all necessary benchmarks and dependencies included. This approach streamlines the testing process, enabling more efficient and automated performance evaluation of the Cheaha system. The containerized version of the Phoronix Test Suite is currently available in the [Gitlab registry](https://gitlab.rc.uab.edu/rc-data-science/community-containers/phoronix-test-suite-benchmarking/container_registry) for testing. You can find the Phoronix Test Suite repository [here](https://gitlab.rc.uab.edu/rc-data-science/community-containers/phoronix-test-suite-benchmarking).

## CPU Performance Testing

[GROMACS](https://www.gromacs.org/) is a software package utilized for evaluating the performance of CPU systems. The following steps demonstrates how to test a node using Phoronix and GROMACS. Note that testing requires access to the entire node.

  1. To perform system testing, request for an exclusive compute node using `srun`.

  ```bash
  $srun --nodes=1 --ntasks-per-node=24 --mem=80GB --time=10:00:00 --partition=intel-dcb --pty /bin/bash
  ```
  
  1. Pull the Phoronix Test Suite using Singularity by obtaining the correct path from this [registry](https://gitlab.rc.uab.edu/rc-data-science/community-containers/phoronix-test-suite-benchmarking/container_registry). For this example, you can name the image file `phoronix-latest.sif`.

  ```bash
  $singularity pull phoronix-latest.sif docker://gitlab.rc.uab.edu:4567/rc-data-science/community-containers/phoronix-test-suite-benchmarking:latest
  ```
  
  1. Run the Singularity image `phoronix-latest.sif` using the `phoronix-test-suite` executable with the `batch-setup` option for initial configuration:

  ```bash
  $singularity run phoronix-latest.sif phoronix-test-suite batch-setup
  ```

  Follow the prompts to complete the setup:
  
  (i) For saving test results in batch mode, enter n (no)

  ```bash
     Save test results when in batch mode (Y/n): n
  ```
  
  (ii) To run all test options, enter y (yes)

  ```bash
     Run all test options (Y/n): y
     Batch settings saved.
  ```

  1. Run the benchmark using the batch-benchmark option with GROMACS version 1.9.0.
  
  ```bash
  $singularity run phoronix-latest.sif phoronix-test-suite batch-benchmark gromacs-1.9.0
  ```

The above command downloads the gromacs-1.9.0 suite and the required sample test, install the Gromacs suite (GROMACS 2024), and begin to perform the testing on the available resources. The below result summarizes the Gromacs performance test. The test is running on an MPI (Message Passing Interface) CPU implementation, meaning it’s using multiple processors in parallel. The simulation is using `water_GMX50_bare` as input, which is a water molecular system. You can see the test is running 3 times to ensure consistency.

### Performance Results

```bash
   2.375, 2.348, 2.351
```

The performance of each run is measured in nanoseconds per day (Ns/day). This metric indicates how many nanoseconds of simulation time can be computed in one day of real time. The average performance of the GROMACS simulation across the three runs is 2.358 Ns/day. The deviation of 0.63% indicates that the three runs produced very similar results, with only a small variation in performance. A low deviation suggests that the test results are consistent and reliable. Note that this metric can be useful for comparing the performance of different hardware setups or GROMACS configurations. The average performance reported is 2.358 nanoseconds per day (Ns/day). This means that, on average, your GROMACS simulation can compute 2.358 nanoseconds of simulation time in one day of real-world time.

This shows that the system is performing consistently, with an average speed of 2.358 Ns/day, and only a small variation across runs. This means your setup is likely stable and efficient for this particular GROMACS simulation.

```bash
$ srun --nodes=1 --ntasks-per-node=24 --mem=120GB --time=10:00:00 --partition=intel-dcb --pty /bin/bash
```

```bash
==========
== CUDA ==
==========
CUDA Version 12.2.2

Container image Copyright (c) 2016-2023, NVIDIA CORPORATION & AFFILIATES. All rights reserved.

This container image and its contents are governed by the NVIDIA Deep Learning Container License.
By pulling and using the container, you accept the terms and conditions of this license:
https://developer.nvidia.com/ngc/nvidia-deep-learning-container-license
A copy of this license is made available in this container at /NGC-DL-CONTAINER-LICENSE for your convenience.

WARNING: The NVIDIA Driver was not detected.  GPU functionality will not be available.
   Use the NVIDIA Container Toolkit to start this container with GPU support; see
   https://docs.nvidia.com/datacenter/cloud-native/ .

    Evaluating External Test Dependencies ..............................................................................................................................................................

Phoronix Test Suite v10.8.4
    Installed:     pts/gromacs-1.9.0

System Information

  PROCESSOR:            2 x Intel Xeon Gold 6126 @ 3.70GHz
  Core Count:           24                                                  
  Extensions:           SSE 4.2 + AVX512CD + AVX2 + AVX + RDRAND + FSGSBASE 
  Cache Size:           38.5 MB                                             
  Microcode:            0x2007006                                           
  Core Family:          Cascade Lake                                        
  Scaling Driver:       intel_pstate performance                            
  GRAPHICS:             mgadrmfb
  Screen:               1024x768         
  MOTHERBOARD:          Dell 0H28RR
  BIOS Version:         2.23.0           
  MEMORY:               768GB
  DISK:                 1000GB PERC H740P Mini
  File-System:          gpfs             
  Disk Scheduler:       DEADLINE         
  OPERATING SYSTEM:     Ubuntu 20.04
  Kernel:               3.10.0-1160.24.1.el7.x86_64 (x86_64) 
  Compiler:             GCC 11.4.0 + CUDA 12.2               
  System Layer:         docker                               

GROMACS 2024:

    pts/gromacs-1.9.0 [Implementation: MPI CPU - Input: water_GMX50_bare]
    Test 1 of 1
    Estimated Trial Run Count:    3                     
    Estimated Time To Completion: 6 Minutes [10:42 CDT] 
        Started Run 1 @ 10:37:24
        Started Run 2 @ 10:39:06
        Started Run 3 @ 10:40:54
    Implementation: MPI CPU - Input: water_GMX50_bare:
        2.375
        2.348
        2.351
    Average: 2.358 Ns Per Day
    Deviation: 0.63%
```

Higher is Better: The larger the number, the faster your simulation is running. For instance, a simulation with 2.358 Ns/day will progress 2.281 nanoseconds in the simulated system for every day that passes in real time.

```bash
GROMACS 2024:
    pts/gromacs-1.8.0 [Implementation: MPI CPU - Input: water_GMX50_bare]
    Test 1 of 1
    Estimated Trial Run Count:    3                     
    Estimated Time To Completion: 5 Minutes [11:34 CDT] 
        Started Run 1 @ 11:30:08
        The test quit with a non-zero exit status.
        Started Run 2 @ 11:30:14
        The test quit with a non-zero exit status.
        Started Run 3 @ 11:30:18
        The test quit with a non-zero exit status.
        E: There are not enough slots available in the system to satisfy the 128
```

## GPU Performance Testing

```bash
$ srun --ntasks=12 --gres=gpu:2 --mem=100GB--time=10:00:00 --partition=amperenodes --pty /bin/bash
$ export CUDA_VISIBLE_DEVICES=0
```

```bash
==========
== CUDA ==
==========

CUDA Version 12.2.2

Container image Copyright (c) 2016-2023, NVIDIA CORPORATION & AFFILIATES. All rights reserved.

This container image and its contents are governed by the NVIDIA Deep Learning Container License.
By pulling and using the container, you accept the terms and conditions of this license:
https://developer.nvidia.com/ngc/nvidia-deep-learning-container-license

A copy of this license is made available in this container at /NGC-DL-CONTAINER-LICENSE for your convenience.

    Evaluating External Test Dependencies ..................................

Phoronix Test Suite v10.8.4
    Installed:     pts/gromacs-1.9.0

GROMACS 2024:
    pts/gromacs-1.9.0
    System Test Configuration
        1: MPI CPU
        2: NVIDIA CUDA GPU
        3: Test All Options
        ** Multiple items can be selected, delimit by a comma. **
        Implementation: 2

System Information
  PROCESSOR:              2 x AMD EPYC 7763 64-Core
    Core Count:           128                                      
    Extensions:           SSE 4.2 + AVX2 + AVX + RDRAND + FSGSBASE 
    Cache Size:           512 MB                                   
    Microcode:            0xa0011d3                                
    Core Family:          Zen 3                                    

  GRAPHICS:               NVIDIA A100 80GB PCIe
    BAR1 / Visible vRAM:  131072 MiB       
    Display Driver:       NVIDIA           
    Screen:               1024x768         

  MOTHERBOARD:            Dell 03WYW4
    BIOS Version:         2.14.1           

  MEMORY:                 512GB

  DISK:                   2 x 3201GB Dell Ent NVMe CM6 MU 3.2TB + 2 x 480GB SK hynix HFS480G32FEH-BA1
    File-System:          gpfs             
    Disk Scheduler:       NONE             

  OPERATING SYSTEM:       Ubuntu 20.04
    Kernel:               3.10.0-1160.24.1.el7.x86_64 (x86_64) 
    Desktop:              Xfce                                 
    Compiler:             GCC 11.4.0 + CUDA 12.2               
    System Layer:         docker                               

GROMACS 2024:
    pts/gromacs-1.9.0 [Implementation: NVIDIA CUDA GPU - Input: water_GMX50_bare]
    Test 1 of 1
    Estimated Trial Run Count:    3                     
    Estimated Time To Completion: 5 Minutes [09:01 CDT] 
        Started Run 1 @ 08:57:06
        Started Run 2 @ 08:57:51
        Started Run 3 @ 08:58:35

    Implementation: NVIDIA CUDA GPU - Input: water_GMX50_bare:
        23.93
        23.816
        23.791

    Average: 23.846 Ns Per Day
    Deviation: 0.31%
```