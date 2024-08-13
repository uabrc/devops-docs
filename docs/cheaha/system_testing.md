# System Performance Testing with Phoronix Test Suite Benchmarks

The Phoronix Test Suite is an open-source benchmarking and comprehensive performance testing tool designed to assess and analyze the performance of hardware systems. It offers a wide range of benchmarks that cover various aspects of system performance, including CPU, GPU, memory, storage, network, file system and many more.

Although the Phoronix Test Suite is available as a module on Cheaha, we need to install or load the missing dependencies required by individual benchmarks. To streamline this process, we are containerizing the Phoronix Test Suite along with the required benchmarks and dependencies. This approach allows us to run the benchmarks directly on both CPU and GPU for comprehensive evaluation. The containerized version of the Phoronix Test Suite is currently available in the [Gitlab registry](https://gitlab.rc.uab.edu/rc-data-science/community-containers/phoronix-test-suite-benchmarking/container_registry) for testing. You can find the Phoronix Test Suite repository [here](https://gitlab.rc.uab.edu/rc-data-science/community-containers/phoronix-test-suite-benchmarking).

## CPU Performance Testing

We have used Gromacs software for testing the performance of multi-core and multi-node CPU.

## GPU Benchmark Testing
