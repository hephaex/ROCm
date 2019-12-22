## ROCm Version History
This file contains archived version history information for the [ROCm project](https://github.com/RadeonOpenCompute/ROCm)

### Current ROCm Version: 2.10
- [New features and enhancements in ROCm v2.10](#new-features-and-enhancements-in-rocm-v210)
- [New features and enhancements in ROCm 2.9](#new-features-and-enhancements-in-rocm-29)
- [New features and enhancements in ROCm 2.8](#new-features-and-enhancements-in-rocm-28)
- [New features and enhancements in ROCm 2.7.2](#new-features-and-enhancements-in-rocm-272)
- [New features and enhancements in ROCm 2.7](#new-features-and-enhancements-in-rocm-27)
- [New features and enhancements in ROCm 2.6](#new-features-and-enhancements-in-rocm-26)
- [New features and enhancements in ROCm 2.5](#new-features-and-enhancements-in-rocm-25)
- [New features and enhancements in ROCm 2.4](#new-features-and-enhancements-in-rocm-24)
- [New features and enhancements in ROCm 2.3](#new-features-and-enhancements-in-rocm-23)
- [New features and enhancements in ROCm 2.2](#new-features-and-enhancements-in-rocm-22)
- [New features and enhancements in ROCm 2.1](#new-features-and-enhancements-in-rocm-21)
- [New features and enhancements in ROCm 2.0](#new-features-and-enhancements-in-rocm-20)
- [New features and enhancements in ROCm 1.9.2](#new-features-and-enhancements-in-rocm-192)
- [New features and enhancements in ROCm 1.9.2](#new-features-and-enhancements-in-rocm-192-1)
- [New features and enhancements in ROCm 1.9.1](#new-features-and-enhancements-in-rocm-191)
- [New features and enhancements in ROCm 1.9.0](#new-features-and-enhancements-in-rocm-190)
- [New features as of ROCm 1.8.3](#new-features-as-of-rocm-183)
- [New features as of ROCm 1.8](#new-features-as-of-rocm-18)
- [New Features as of ROCm 1.7](#new-features-as-of-rocm-17)
- [New Features as of ROCm 1.5](#new-features-as-of-rocm-15)


### New features and enhancements in ROCm v2.10
#### rocBLAS Support for Complex GEMM
The rocBLAS library is a gpu-accelerated implementation of the standard Basic Linear Algebra Subroutines (BLAS). rocBLAS is designed to enable you to develop algorithms, including high performance computing, image analysis, and machine learning.

In the AMD ROCm release v2.10, support is extended to the General Matrix Multiply (GEMM) routine for multiple small matrices processed simultaneously for rocBLAS in AMD Radeon Instinct MI50. Both single and double precision, CGEMM and ZGEMM, are now supported in rocBLAS.

#### Support for SLES 15 SP1
In the AMD ROCm v2.10 release, support is added for SUSE Linux® Enterprise Server (SLES) 15 SP1. SLES is a modular operating system for both multimodal and traditional IT.

#### Code Marker Support for rocProfiler and rocTracer Libraries
Code markers provide the external correlation ID for the calling thread. This function indicates that the calling thread is entering and leaving an external API region.

### New features and enhancements in ROCm 2.9

#### Initial release for Radeon Augmentation Library(RALI)
The AMD Radeon Augmentation Library (RALI) is designed to efficiently decode and process images from a variety of storage formats and modify them through a processing graph programmable by the user. RALI currently provides C API.

#### Quantization in MIGraphX v0.4
MIGraphX 0.4 introduces support for fp16 and int8 quantization. For additional details, as well as other new MIGraphX features, see [MIGraphX documentation](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Getting-started:-using-the-new-features-of-MIGraphX-0.4).

#### rocSparse csrgemm
csrgemm enables the user to perform matrix-matrix multiplication with two sparse matrices in CSR format.

#### Singularity Support
ROCm 2.9 adds support for Singularity container version 2.5.2.

#### Initial release of rocTX
ROCm 2.9 introduces rocTX, which provides a C API for code markup for performance profiling.  This initial release of rocTX supports annotation of code ranges and ASCII markers.  For an example, see this [code](https://github.com/ROCm-Developer-Tools/roctracer/blob/amd-master/test/MatrixTranspose_test/MatrixTranspose.cpp).

#### Added support for Ubuntu 18.04.3
Ubuntu 18.04.3 is now supported in ROCm 2.9.



### New features and enhancements in ROCm 2.8

#### Support for NCCL2.4.8 API
Implements ncclCommAbort() and ncclCommGetAsyncError() to match the NCCL 2.4.x API

### New features and enhancements in ROCm 2.7.2

This release is a hotfix for ROCm release 2.7.

#### Issues fixed in ROCm 2.7.2

##### A defect in upgrades from older ROCm releases has been fixed.

##### rocprofiler --hiptrace and --hsatrace fails to load roctracer library
In ROCm 2.7.2, rocprofiler --hiptrace and --hsatrace fails to load roctracer library defect has been fixed.  
To generate traces, please provide directory path also using the parameter: -d <$directoryPath> for example:
```shell
/opt/rocm/bin/rocprof  --hsa-trace -d $PWD/traces /opt/rocm/hip/samples/0_Intro/bit_extract/bit_extract
  ```
All traces and results will be saved under $PWD/traces path

#### Upgrading from ROCm 2.7 to 2.7.2

To upgrade, please remove 2.7 completely as specified [for ubuntu](#how-to-uninstall-from-ubuntu-1604-or-Ubuntu-1804) or [for centos/rhel](#how-to-uninstall-rocm-from-centosrhel-76), and install 2.7.2 as per instructions [install instructions](#installing-from-amd-rocm-repositories)

#### Other notes

  To use rocprofiler features, the following steps need to be completed before using rocprofiler:

  ##### Step-1: Install roctracer

###### Ubuntu 16.04 or Ubuntu 18.04:

  ```shell
  sudo apt install roctracer-dev
  ```

######  CentOS/RHEL 7.6:

  ```shell
  sudo yum install roctracer-dev
  ```
  ##### Step-2: Add /opt/rocm/roctracer/lib to LD_LIBRARY_PATH
  
### New features and enhancements in ROCm 2.7

#### [rocFFT] Real FFT Functional
Improved real/complex 1D even-length transforms of unit stride. Performance improvements of up to 4.5x are observed. Large problem sizes should see approximately 2x.

#### rocRand Enhancements and Optimizations
- Added support for new datatypes: uchar, ushort, half.
- Improved performance on "Vega 7nm" chips, such as on the Radeon Instinct MI50
- mtgp32 uniform double performance changes due generation algorithm standardization. Better quality random numbers now generated with 30% decrease in performance
- Up to 5% performance improvements for other algorithms

#### RAS
Added support for RAS on Radeon Instinct MI50, including:
- Memory error detection
- Memory error detection counter

#### ROCm-SMI enhancements
Added ROCm-SMI CLI and LIB support for FW version, compute running processes, utilization rates, utilization counter, link error counter, and unique ID.

### New features and enhancements in ROCm 2.6

#### ROCmInfo enhancements
ROCmInfo was extended to do the following:
For ROCr API call errors including initialization determine if the error could be explained by:
- ROCk (driver) is not loaded / available
- User does not have membership in appropriate group - "video"
- If not above print the error string that is mapped to the returned error code
- If no error string is available, print the error code in hex

#### Thrust - Functional Support on Vega20
ROCm2.6 contains the first official release of rocThrust and hipCUB. rocThrust is a port of thrust, a parallel algorithm library. hipCUB is a port of CUB, a reusable software component library. Thrust/CUB has been ported to the HIP/ROCm platform to use the rocPRIM library. The HIP ported library works on HIP/ROCm platforms.

Note: rocThrust and hipCUB library replaces https://github.com/ROCmSoftwarePlatform/thrust (hip-thrust), i.e. hip-thrust has been separated into two libraries, rocThrust and hipCUB. Existing hip-thrust users are encouraged to port their code to rocThrust and/or hipCUB. Hip-thrust will be removed from official distribution later this year.

#### MIGraphX v0.3
MIGraphX optimizer adds support to read models frozen from Tensorflow framework. Further details and an example usage at https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Getting-started:-using-the-new-features-of-MIGraphX-0.3

#### MIOpen 2.0
- This release contains several new features including an immediate mode for selecting convolutions, bfloat16 support, new layers, modes, and algorithms.
- MIOpenDriver, a tool for benchmarking and developing kernels is now shipped with MIOpen.
BFloat16 now supported in HIP requires an updated rocBLAS as a GEMM backend.
- Immediate mode API now provides the ability to quickly obtain a convolution kernel.
- MIOpen now contains HIP source kernels and implements the ImplicitGEMM kernels. This is a new feature and is currently disabled by default. Use the environmental variable "MIOPEN_DEBUG_CONV_IMPLICIT_GEMM=1" to activation this feature. ImplicitGEMM requires an up to date HIP version of at least 1.5.9211.
- A new "loss" catagory of layers has been added, of which, CTC loss is the first. See the API reference for more details.
2.0 is the last release of active support for gfx803 architectures. In future releases, MIOpen will not actively debug and develop new features specifically for gfx803.
- System Find-Db in memory cache is disabled by default. Please see build instructions to enable this feature.
Additional documentation can be found here: https://rocmsoftwareplatform.github.io/MIOpen/doc/html/

#### Bloat16 software support in rocBLAS/Tensile
Added mixed precision bfloat16/IEEE f32 to gemm_ex. The input and output matrices are bfloat16. All arithmetic is in IEEE f32.

#### AMD Infinity Fabric™ Link enablement
The ability to connect four Radeon Instinct MI60 or Radeon Instinct MI50 boards in two hives or two Radeon Instinct MI60 or Radeon Instinct MI50 boards in four hives via AMD Infinity Fabric™ Link GPU interconnect technology has been added.

#### ROCm-smi features and bug fixes
  - mGPU & Vendor check
  - Fix clock printout if DPM is disabled
  - Fix finding marketing info on CentOS
  - Clarify some error messages

#### ROCm-smi-lib enhancements
- Documentation updates
- Improvements to *name_get functions

#### RCCL2 Enablement
RCCL2 supports collectives intranode communication using PCIe, Infinity Fabric™, and pinned host memory, as well as internode communication using Ethernet (TCP/IP sockets) and Infiniband/RoCE (Infiniband Verbs).  Note: For Infiniband/RoCE, RDMA is not currently supported.

#### rocFFT enhancements
- Added: Debian package with FFT test, benchmark, and sample programs
- Improved: hipFFT interfaces
- Improved: rocFFT CPU reference code, plan generation code and logging code

### New features and enhancements in ROCm 2.5

#### UCX 1.6 support
Support for UCX version 1.6 has been added.

#### BFloat16 GEMM in rocBLAS/Tensile
Software support for BFloat16 on Radeon Instinct MI50, MI60 has been added.  This includes:
- Mixed precision GEMM with BFloat16 input and output matrices, and all arithmetic in IEEE32 bit
- Input matrix values are converted from BFloat16 to IEEE32 bit, all arithmetic and accumulation is IEEE32 bit. Output values are rounded from IEEE32 bit to BFloat16
- Accuracy should be correct to 0.5 ULP

#### ROCm-SMI enhancements
CLI support for querying the memory size, driver version, and firmware version has been added to ROCm-smi.

#### [PyTorch] multi-GPU functional support (CPU aggregation/Data Parallel)
Multi-GPU support is enabled in PyTorch using Dataparallel path for versions of PyTorch built using the 06c8aa7a3bbd91cda2fd6255ec82aad21fa1c0d5 commit or later.

#### rocSparse optimization on Radeon Instinct MI50 and MI60
This release includes performance optimizations for csrsv routines in the rocSparse library.

#### [Thrust] Preview
Preview release for early adopters. rocThrust is a port of thrust, a parallel algorithm library. Thrust has been ported to the HIP/ROCm platform to use the rocPRIM library. The HIP ported library works on HIP/ROCm platforms.

Note: This library will replace https://github.com/ROCmSoftwarePlatform/thrust in a future release. The package for rocThrust (this library) currently conflicts with version 2.5 package of thrust. They should not be installed together.

#### Support overlapping kernel execution in same HIP stream
HIP API has been enhanced to allow independent kernels to run in parallel on the same stream.

#### AMD Infinity Fabric&#x2122; Link enablement
The ability to connect four Radeon Instinct MI60 or Radeon Instinct MI50 boards in one hive via AMD Infinity Fabric™ Link GPU interconnect technology has been added.
### New features and enhancements in ROCm 2.4

#### TensorFlow 2.0 support
ROCm 2.4 includes the enhanced compilation toolchain and a set of bug fixes to support TensorFlow 2.0 features natively

#### AMD Infinity Fabric&#x2122; Link enablement
ROCm 2.4 adds support to connect two Radeon Instinct MI60 or Radeon Instinct MI50 boards via AMD Infinity Fabric&#x2122; Link GPU interconnect technology.

### New features and enhancements in ROCm 2.3

#### Mem usage per GPU
Per GPU memory usage is added to rocm-smi.
Display information regarding used/total bytes for VRAM, visible VRAM and GTT, via the --showmeminfo flag

#### MIVisionX, v1.1 - ONNX
ONNX parser changes to adjust to new file formats

#### MIGraphX, v0.2
MIGraphX 0.2 supports the following new features:
* New Python API
* Support for additional ONNX operators and fixes that now enable a large set of Imagenet models
* Support for RNN Operators
* Support for multi-stream Execution
* [Experimental] Support for Tensorflow frozen protobuf files

See: [Getting-started:-using-the-new-features-of-MIGraphX-0.2](https://github.com/ROCmSoftwarePlatform/AMDMIGraphX/wiki/Getting-started:-using-the-new-features-of-MIGraphX-0.2) for more details

#### MIOpen, v1.8 - 3d convolutions and int8
* This release contains full 3-D convolution support and int8 support for inference.
* Additionally, there are major updates in the performance database for major models including those found in Torchvision.

See: [MIOpen releases](https://github.com/ROCmSoftwarePlatform/MIOpen/releases)

#### Caffe2 -  mGPU support
Multi-gpu support is enabled for Caffe2.

#### rocTracer library, ROCm tracing API for collecting runtimes API and asynchronous GPU activity traces
HIP/HCC domains support is introduced in rocTracer library.

#### BLAS -  Int8 GEMM performance, Int8 functional and performance
Introduces support and performance optimizations for Int8 GEMM, implements TRSV support, and includes improvements and optimizations with Tensile.

#### Prioritized L1/L2/L3 BLAS (functional)
Functional implementation of BLAS L1/L2/L3 functions

#### BLAS - tensile optimization
Improvements and optimizations with tensile

#### MIOpen Int8 support
Support for int8

### New features and enhancements in ROCm 2.2

#### rocSparse Optimization on Vega20
Cache usage optimizations for csrsv (sparse triangular solve), coomv
(SpMV in COO format) and ellmv (SpMV in ELL format) are available.

#### DGEMM and DTRSM Optimization
Improved DGEMM performance for reduced matrix sizes (k=384, k=256)

#### Caffe2
Added support for multi-GPU training

### New features and enhancements in ROCm 2.1

#### RocTracer v1.0 preview release – 'rocprof' HSA runtime tracing and statistics support -
Supports HSA API tracing and HSA asynchronous GPU activity including kernels execution and memory copy

#### Improvements to ROCM-SMI tool -
Added support to show real-time PCIe bandwidth usage via the -b/--showbw flag

#### DGEMM Optimizations -
Improved DGEMM performance for large square and reduced matrix sizes (k=384, k=256)

### New features and enhancements in ROCm 2.0

#### Adds support for RHEL 7.6 / CentOS 7.6 and Ubuntu 18.04.1

#### Adds support for Vega 7nm, Polaris 12 GPUs

#### Introduces MIVisionX
* A comprehensive computer vision and machine intelligence libraries, utilities and applications bundled into a single toolkit.

#### Improvements to ROCm Libraries
* rocSPARSE & hipSPARSE
* rocBLAS with improved DGEMM efficiency on Vega 7nm

#### MIOpen
* This release contains general bug fixes and an updated performance database
* Group convolutions backwards weights performance has been improved
* RNNs now support fp16

#### Tensorflow multi-gpu and Tensorflow FP16 support for Vega 7nm
* TensorFlow v1.12 is enabled with fp16 support

#### PyTorch/Caffe2 with Vega 7nm Support
* fp16 support is enabled
* Several bug fixes and performance enhancements
* Known Issue: breaking changes are introduced in ROCm 2.0 which are not addressed upstream yet. Meanwhile, please continue to use ROCm fork at https://github.com/ROCmSoftwarePlatform/pytorch

#### Improvements to ROCProfiler tool
* Support for Vega 7nm

#### Support for hipStreamCreateWithPriority
* Creates a stream with the specified priority. It creates a stream on which enqueued kernels have a different priority for execution compared to kernels enqueued on normal priority streams. The priority could be higher or lower than normal priority streams.

#### OpenCL 2.0 support
* ROCm 2.0 introduces full support for kernels written in the OpenCL 2.0 C language on certain devices and systems.  Applications can detect this support by calling the “clGetDeviceInfo” query function with “parame_name” argument set to “CL_DEVICE_OPENCL_C_VERSION”.  In order to make use of OpenCL 2.0 C language features, the application must include the option “-cl-std=CL2.0” in options passed to the runtime API calls responsible for compiling or building device programs.  The complete specification for the OpenCL 2.0 C language can be obtained using the following link: https://www.khronos.org/registry/OpenCL/specs/opencl-2.0-openclc.pdf

#### Improved Virtual Addressing (48 bit VA) management for Vega 10 and later GPUs
* Fixes Clang AddressSanitizer and potentially other 3rd-party memory debugging tools with ROCm
* Small performance improvement on workloads that do a lot of memory management
* Removes virtual address space limitations on systems with more VRAM than system memory

#### Kubernetes support

### New features and enhancements in ROCm 1.9.2
#### RDMA(MPI) support on Vega 7nm
* Support ROCnRDMA based on Mellanox InfiniBand

#### Improvements to HCC
* Improved link time optimization

#### Improvements to ROCProfiler tool
* General bug fixes and implemented versioning APIs

### New features and enhancements in ROCm 1.9.2
#### RDMA(MPI) support on Vega 7nm
* Support ROCnRDMA based on Mellanox InfiniBand

#### Improvements to HCC
* Improved link time optimization

#### Improvements to ROCProfiler tool
* General bug fixes and implemented versioning APIs

#### Critical bug fixes

### New features and enhancements in ROCm 1.9.1
#### Added DPM support to Vega 7nm
* Dynamic Power Management feature is enabled on Vega 7nm.

#### Fix for 'ROCm profiling' that used to fail with a “Version mismatch between HSA runtime and libhsa-runtime-tools64.so.1” error

### New features and enhancements in ROCm 1.9.0

#### Preview for Vega 7nm
* Enables developer preview support for Vega 7nm

#### System Management Interface
* Adds support for the ROCm SMI (System Management Interface) library, which provides monitoring and management capabilities for AMD GPUs.

#### Improvements to HIP/HCC
* Support for gfx906
* Added deprecation warning for C++AMP.  This will be the last version of HCC supporting C++AMP.
* Improved optimization for global address space pointers passing into a GPU kernel
* Fixed several race conditions in the HCC runtime
* Performance tuning to the unpinned copy engine
* Several codegen enhancement fixes in the compiler backend

#### Preview for rocprof Profiling Tool
Developer preview (alpha) of profiling tool rocProfiler. It includes a command-line front-end, `rpl_run.sh`, which enables:
* Cmd-line tool for dumping public per kernel perf-counters/metrics and kernel timestamps
* Input file with counters list and kernels selecting parameters
* Multiple counters groups and app runs supported
* Output results in CSV format

The tool can be installed from the `rocprofiler-dev` package. It will be installed into: `/opt/rocm/bin/rpl_run.sh`

#### Preview for rocr Debug Agent rocr_debug_agent
The ROCr Debug Agent is a library that can be loaded by ROCm Platform Runtime to provide the following functionality:
* Print the state for wavefronts that report memory violation or upon executing a "s_trap 2" instruction.
* Allows SIGINT (`ctrl c`) or SIGTERM (`kill -15`) to print wavefront state of aborted GPU dispatches.
* It is enabled on Vega10 GPUs on ROCm1.9.

The ROCm1.9 release will install the ROCr Debug Agent library at `/opt/rocm/lib/librocr_debug_agent64.so`


#### New distribution support

* Binary package support for Ubuntu 18.04

#### ROCm 1.9 is ABI compatible with KFD in upstream Linux kernels.
Upstream Linux kernels support the following GPUs in these releases:
4.17: Fiji, Polaris 10, Polaris 11
4.18: Fiji, Polaris 10, Polaris 11, Vega10

Some ROCm features are not available in the upstream KFD:
* More system memory available to ROCm applications
* Interoperability between graphics and compute
* RDMA
* IPC

To try ROCm with an upstream kernel, install ROCm as normal, but do not install the rock-dkms package. Also add a udev rule to control `/dev/kfd` permissions:

```
    echo 'SUBSYSTEM=="kfd", KERNEL=="kfd", TAG+="uaccess", GROUP="video"' | sudo tee /etc/udev/rules.d/70-kfd.rules
```

### New features as of ROCm 1.8.3

* ROCm 1.8.3 is a minor update meant to fix compatibility issues on Ubuntu releases running kernel 4.15.0-33

### New features as of ROCm 1.8

#### DKMS driver installation

 * Debian packages are provided for DKMS on Ubuntu
 * RPM packages are provided for CentOS/RHEL 7.4 and 7.5 support
 * See the [ROCT-Thunk-Interface](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface/tree/roc-1.8.x) and [ROCK-Kernel-Driver](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver/tree/roc-1.8.x) for additional documentation on driver setup

#### New distribution support

 * Binary package support for Ubuntu 16.04 and 18.04
 * Binary package support for CentOS 7.4 and 7.5
 * Binary package support for RHEL 7.4 and 7.5

#### Improved OpenMPI via UCX support

 * UCX support for OpenMPI
 * ROCm RDMA

### New Features as of ROCm 1.7

#### DKMS driver installation

 * New driver installation uses Dynamic Kernel Module Support (DKMS)
 * Only amdkfd and amdgpu kernel modules are installed to support AMD hardware
 * Currently only Debian packages are provided for DKMS (no Fedora suport available)
 * See the [ROCT-Thunk-Interface](https://github.com/RadeonOpenCompute/ROCT-Thunk-Interface/tree/roc-1.7.x) and [ROCK-Kernel-Driver](https://github.com/RadeonOpenCompute/ROCK-Kernel-Driver/tree/roc-1.7.x) for additional documentation on driver setup

### New Features as of ROCm 1.5

#### Developer preview of the new OpenCL 1.2 compatible language runtime and compiler

 * OpenCL 2.0 compatible kernel language support with OpenCL 1.2 compatible
   runtime
 * Supports offline ahead of time compilation today;
   during the Beta phase we will add in-process/in-memory compilation.

#### Binary Package support for Ubuntu 16.04

#### Binary Package support for Fedora 24 is not currently available

#### Dropping binary package support for Ubuntu 14.04, Fedora 23

#### IPC support
