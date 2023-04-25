cmake_minimum_required(VERSION 3.21)
project(lodepng)
enable_language(CXX)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -W -Wall -Wextra -ansi -pedantic")
include_directories(${PROJECT_SOURCE_DIR})
add_executable(bmp2png examples/example_bmp2png.cpp lodepng.cpp)
