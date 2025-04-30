# Minimum CMake version required
cmake_minimum_required(VERSION 3.19)
 
# Project name and language
project(HeatEquation LANGUAGES CXX)
 
# Specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)


find_package(AMReX REQUIRED)
#find_package(IntelSYCL REQUIRED)
find_package(MKL CONFIG REQUIRED PATHS $ENV{MKLROOT})
 
# Add the executable
add_executable(HeatEquation main.cpp)

target_link_libraries(HeatEquation PUBLIC MKL::MKL "C:/Program Files (x86)/Intel/oneAPI/mkl/latest/lib/mkl_sycl_rng_dll.lib")

#target_link_libraries(HeatEquation PUBLIC SYCL)
 
target_link_libraries(HeatEquation PRIVATE AMReX::amrex)