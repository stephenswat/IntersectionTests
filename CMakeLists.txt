 cmake_minimum_required(VERSION 3.11)

project(Hyperplane VERSION 0.0 LANGUAGES CXX)

find_package(Eigen3 REQUIRED)
set(Boost_NO_BOOST_CMAKE ON) 
find_package(Boost 1.69 REQUIRED COMPONENTS timer program_options unit_test_framework)
find_package(Vc 1.4.1 REQUIRED) 

set(CMAKE_INSTALL_INCLUDEDIR ${CMAKE_INSTALL_PREFIX}/include)
set(CMAKE_BENCH_INCLUDEDIR ${CMAKE_INSTALL_PREFIX}/benchmark/include)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_INSTALL_PREFIX}/lib)
set(CMAKE_INSTALL_LIBDIR ${CMAKE_INSTALL_PREFIX}/lib)

# General compile options
add_compile_options(
       -O3 --std=c++17
       #-L/usr/lib64/ -l:libVc.a
       #-Wall -Wextra -Wshadow -fstrict-aliasing -Wno-deprecated-declarations -Wstrict-aliasing
)

# Extra vectorization options
add_compile_options(
       #-march=native -msse -msse2 -msse3 -msse4 -mavx -mavx2
       #-msse -msse2
)

add_subdirectory(src)
add_subdirectory(benchmark)


