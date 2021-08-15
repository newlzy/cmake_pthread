
cmake_minimum_required(VERSION 3.10)
project(01 VERSION 1.0)

#设置c++标准
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

#提供一个选项开关，用户可以任意选择。
option(USE_MYMATH "注释文档" ON)

#将包含目录添加到构建中
include_directories(pthread/include)

#此命令用于查找库
find_library(pthread_lib NAMES pthread PATHS ./pthread)

#添加链接器将在其中查找库的目录
link_directories (D:/jiang/练习代码/多线程/cmake/01/01/pthread/lib/x64)

# 使用指定的源文件向项目添加可执行文件
add_executable(01 01.cpp)

#将pthread_lib 这个变量设置在THIRDPARTY_LIBRARIES 中 
set(THIRDPARTY_LIBRARIES ${pthread_lib})

#//链接库到可执行文件。PROJECT_NAME项目名称
#target_link_libraries(${PROJECT_NAME} ${pthread})

#将包含目录添加到目标。
#PROJECT_BINARY_DIR:为项目构建目录的完整路径。
#EXTRA_INCLUDES类似地用于可选的头文件
target_include_directories(01 PUBLIC
                          "${PROJECT_BINARY_DIR}"
                          "${EXTRA_INCLUDES}"
                          )