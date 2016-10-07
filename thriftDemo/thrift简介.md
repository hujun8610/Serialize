# Thrift简介

## 安装
安装环境为ubuntu,运行如下命令安装:
```shell
sudo apt-get install automake bison flex g++ git libboost1.55-all-dev libevent-dev libssl-dev libtool make pkg-config
sudo apt-get install libglib2.0-dev

./configure
make 
sudo make install
```

使用thrift的步骤如下所示：
1. 依照thrift的idl语法编写idl文件。编辑 shared.thrift文件及tutorial.thrift文件。
2. 运行如下命令：`thrift -r --gen cpp tutorial.thrift`，生成的文件在文件夹gen-cpp中,注意生成的Calculator_server.skeleton.cpp及SharedService_server.skeleton.cpp文件存放于后面创建的文件夹cpp中。
3.创建common目录，用于存放thrift生成的.cpp文件（头文件的路径不变）。
4.创建cpp目录，编辑CppClient.cpp及 CppServer.cpp 文件并保存。
5.编写CMakeLists.txt文件，内容如下：
```
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
```
6. 按照CMake推荐的方式编译工程生成CppClient以及 CppServer即可。

##参考
http://thrift.apache.org/tutorial/cpp






