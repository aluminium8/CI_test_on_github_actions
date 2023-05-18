cmake_minimum_required(VERSION 3.13)
project(test_cmake CXX)
find_package(Boost REQUIRED)

message("BOOST include path: ${Boost_INCLUDE_DIRS}")
message("BOOST library path: ${Boost_LIBRARRY_DIRS}")


include_directories( ${Boost_INCLUDE_DIRS} )

# make library of function "greet"
add_library(greet_func STATIC src/say_hello.cpp src/say_hello.cpp)

add_executable(greet_main src/greet_main)



add_executable(boost_compile_test src/boost_compile_test.cpp)

# a.outを作成する際にlibgreetings.soをリンク
target_link_libraries(greet_main greet_func)
target_link_libraries(boost_complile_test ${Boost_LIBRARY_DIRS})