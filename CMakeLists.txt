cmake_minimum_required(VERSION 3.11)
project(cceh)
set(CMAKE_CXX_STANDARD 17)
add_library(cceh "")
target_sources(cceh
        PRIVATE
        "CCEH-PMDK/src/CCEH.cpp"
        "CCEH-PMDK/src/CCEH.cpp"
        "CCEH-PMDK/src/hash.h"
        "CCEH-PMDK/src/pair.h"
        "CCEH-PMDK/src/util.h")

find_library(pmem REQUIRED)
find_library(pmemobj REQUIRED)
find_library(pthread REQUIRED)

target_link_libraries(cceh pmemobj pmem pthread)

add_executable(cceh_test CCEH-PMDK/src/test.cpp)
target_link_libraries(cceh_test cceh)