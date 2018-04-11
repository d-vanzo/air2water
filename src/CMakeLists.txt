# CMake project file for air2water

cmake_minimum_required (VERSION 2.8)
project (air2water)
enable_language (Fortran)

# detect operating system and host processor
message(STATUS "We are on a ${CMAKE_SYSTEM_NAME} system")
message(STATUS "The host processor is ${CMAKE_HOST_SYSTEM_PROCESSOR}")

# this is where we will place the Fortran module files
set(CMAKE_Fortran_MODULE_DIRECTORY ${PROJECT_BINARY_DIR}/modules)

#
set(CMAKE_Fortran_FLAGS "-ffree-form -ffree-line-length-0")

if(CMAKE_Fortran_COMPILER_ID MATCHES Intel)
    set(CMAKE_Fortran_FLAGS         "${CMAKE_Fortran_FLAGS} -fpp -Wall")
    set(CMAKE_Fortran_FLAGS_DEBUG   "-g -traceback")
    set(CMAKE_Fortran_FLAGS_RELEASE "-O3 -ip -xHOST")
endif()

if(CMAKE_Fortran_COMPILER_ID MATCHES GNU)
    set(CMAKE_Fortran_FLAGS         "${CMAKE_Fortran_FLAGS} -cpp -Wall")
    set(CMAKE_Fortran_FLAGS_DEBUG   "-O0 -g3")
    set(CMAKE_Fortran_FLAGS_RELEASE "-Ofast -ffast-math -march=native")
endif()

# we set default to Release build type
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Release")
endif()
add_definitions(-DCMAKE_BUILD_TYPE="Release")

add_executable(
    air2water
    AIR2WATER_MAIN.f90
    AIR2WATER_MODULES.f90
    AIR2WATER_READ.f90
    AIR2WATER_RUNMODE.f90
    AIR2WATER_SUBROUTINES.f90
    )