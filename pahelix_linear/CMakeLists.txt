cmake_minimum_required(VERSION 3.6)
project(LinearX)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -O3 -fPIC")

add_subdirectory(third-party/pybind11)

include_directories("${CMAKE_CURRENT_SOURCE_DIR}/linear_x")

file(GLOB src
    "${CMAKE_CURRENT_SOURCE_DIR}/linear_x/*/*.cpp")
add_library(linear_x_core STATIC ${src})

pybind11_add_module(linear_x
    ${CMAKE_CURRENT_SOURCE_DIR}/linear_x/linear_x.cpp)
target_link_libraries(linear_x PRIVATE pybind11::module linear_x_core)

