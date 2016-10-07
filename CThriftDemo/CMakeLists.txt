cmake_minimum_required (VERSION 3.0)

project(thriftDemo)

set(CMAKE_VERBOSE_MAKEFILE on)
aux_source_directory(./common COMMONSRC)

include_directories(
    gen-c_glib
    /usr/local/include/thrift/
    /usr/include
    )
link_directories(/usr/local/lib/)

add_executable(CServer ./src/c_glib_server.c ${COMMONSRC})
target_link_libraries(CServer thrift)

add_executable(CClient ./src/c_glib_client.c ${COMMONSRC})
target_link_libraries(CClient thrift)
