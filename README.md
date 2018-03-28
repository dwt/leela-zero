[![Linux Build Status](https://travis-ci.org/gcp/leela-zero.svg?branch=next)](https://travis-ci.org/gcp/leela-zero)
[![Windows Build Status](https://ci.appveyor.com/api/projects/status/pf1hcgly8f1a8iu0/branch/next?svg=true)](https://ci.appveyor.com/project/gcp/leela-zero/branch/next)

# What

This repository is a custom version of Leela Zero for [Lizzie](https://github.com/featurecat/lizzie). If you are running Windows 64-bit, the binary has already been compiled for you [here](https://github.com/featurecat/lizzie/releases). Otherwise, you will need to compile it from this repository by following the instructions below.

# Compiling

## Requirements

* GCC, Clang or MSVC, any C++14 compiler
* Boost 1.58.x or later, headers and program_options library (libboost-dev & libboost-program-options-dev on Debian/Ubuntu)
* BLAS Library: OpenBLAS (libopenblas-dev) or (optionally) Intel MKL
* zlib library (zlib1g & zlib1g-dev on Debian/Ubuntu)
* Standard OpenCL C headers (opencl-headers on Debian/Ubuntu, or at
https://github.com/KhronosGroup/OpenCL-Headers/tree/master/opencl22/)
* OpenCL ICD loader (ocl-icd-libopencl1 on Debian/Ubuntu, or reference implementation at https://github.com/KhronosGroup/OpenCL-ICD-Loader)
* An OpenCL capable device, preferably a very, very fast GPU, with recent
drivers is strongly recommended (OpenCL 1.2 support should be enough,
even OpenCL 1.1 might work). If you do not have a GPU, modify config.h in the
source and remove the line that says "#define USE_OPENCL".
* The program has been tested on Windows, Linux and macOS.

## Example of compiling and running - Ubuntu

    # Test for OpenCL support & compatibility
    sudo apt install clinfo && clinfo

    # Clone github repo
    git clone https://github.com/featurecat/leela-zero
    cd leela-zero/src
    sudo apt install libboost-dev libboost-program-options-dev libopenblas-dev opencl-headers ocl-icd-libopencl1 ocl-icd-opencl-dev zlib1g-dev
    make

## Example of compiling and running - macOS

    # Clone github repo
    git clone https://github.com/featurecat/leela-zero
    cd leela-zero/src
    brew install boost
    make

## Example of compiling and running - Windows

    # Clone github repo
    git clone https://github.com/featurecat/leela-zero
    cd leela-zero
    cd msvc
    Double-click the leela-zero2015.sln or leela-zero2017.sln corresponding
    to the Visual Studio version you have.
    # Build from Visual Studio 2015 or 2017

## Example of compiling and running - CMake (macOS/Ubuntu)

    # Clone github repo
    git clone https://github.com/featurecat/leela-zero
    cd leela-zero
    git submodule update --init --recursive

    # Use stand alone directory to keep source dir clean
    mkdir build && cd build
    cmake ..
    make leelaz
