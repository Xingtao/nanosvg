cmake_minimum_required(VERSION 3.10 FATAL_ERROR)

project(svgtest VERSION 1.0 LANGUAGES CXX)
set(CMAKE_VERBOSE_MAKEFILE OFF)

get_filename_component(PROJECT_DIR ${CMAKE_CURRENT_SOURCE_DIR} DIRECTORY)
list(INSERT CMAKE_MODULE_PATH 0 ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
# set(STREAMLET_TOP_CMAKE_DIR "${CMAKE_CURRENT_LIST_DIR}/cmake" CACHE PATH "cmake path")
# list(APPEND CMAKE_MODULE_PATH ${STREAMLET_TOP_CMAKE_DIR})

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(CMAKE_CXX_EXTENSIONS OFF)

#### Dependencies ##############################################
set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

## streamlet
set(bin svgtest.out)
add_executable(${bin} example/test.cpp)
target_link_directories(${bin} PUBLIC m)
target_include_directories(${bin}
  PUBLIC ${CMAKE_SOURCE_DIR}/src ${CMAKE_SOURCE_DIR}/example)
