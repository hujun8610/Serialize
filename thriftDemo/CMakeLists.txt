cmake_minimum_required (VERSION 3.0)

project(thriftDemo)

set(CMAKE_VERBOSE_MAKEFILE on)
aux_source_directory(./common COMMONSRC)

include_directories(
    gen-cpp/
    /usr/local/include/thrift/
    )
link_directories(/usr/local/lib/)

add_executable(CppServer ./cpp/CppServer.cpp ${COMMONSRC})
target_link_libraries(CppServer thrift)

add_executable(CppClient ./cpp/CppClient.cpp ${COMMONSRC})
target_link_libraries(CppClient thrift)


