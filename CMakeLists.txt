cmake_minimum_required(VERSION 2.8)
project(onerow)

list(APPEND CMAKE_MODULE_PATH "${CMAKE_CURRENT_LIST_DIR}/cmake")
find_package(CPLEX REQUIRED)
include_directories(${CPLEX_INCLUDE_DIR})

find_package(GMP REQUIRED)
find_package(OpenMP REQUIRED)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_CXX_FLAGS} -O3")
set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS} ${OpenMP_C_FLAGS} -O3")

include_directories(${gtest_SOURCE_DIR}/include)
include_directories(onerow/library/include)
include_directories(qxx/include)

add_subdirectory(googletest/googletest)
add_subdirectory(onerow/benchmark)
add_subdirectory(onerow/library)
add_subdirectory(qxx)
