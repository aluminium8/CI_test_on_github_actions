cmake_minimum_required(VERSION 3.13)
project(test_cmake CXX)

# make library of function "greet"
add_library(greet_func STATIC src/say_hello.cpp src/say_hello.cpp)

add_executable(greet_main src/greet_main)
# a.outを作成する際にlibgreetings.soをリンク
target_link_libraries(greet_main greet_func)
