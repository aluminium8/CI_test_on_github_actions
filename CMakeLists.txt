cmake_minimum_required(VERSION 3.13)
project(test_cmake CXX)
find_package(Boost REQUIRED)

message("BOOST include path: ${BOOST_INCLUDE_DIRS}")
message("BOOST library path: ${BOOST_LIBRARRY_DIRS}")


include_directories( ${BOOST_INCLUDE_DIRS} )

# make library of function "greet"
add_library(greet_func STATIC src/say_hello.cpp src/say_hello.cpp)

add_executable(greet_main src/greet_main)



add_executable(boost_link_test src/boost_test.cpp)

# a.outを作成する際にlibgreetings.soをリンク
target_link_libraries(greet_main greet_func)
target_link_libraries(boost_link_test ${BOOST_LIBRARY_DIRS})