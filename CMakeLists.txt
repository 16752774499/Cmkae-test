# 相关教程链接https://www.subingwen.cn/cmake/CMake-primer/
# 指定cmake版本，必须比本地版本低或持平
cmake_minimum_required(VERSION 3.10)

# 项目名称
project(test)

# 添加可执行程序，参数1为可执行程序命名，参数2[]为生成可执行文件所需源文件
# add_executable(app  add.c div.c main.c mult.c sub.c)
# set可以定义变量，也可以设置当前c++编译器标准,也可以指定输出路径
# set(SRC_LIST add.c div.c main.c mult.c sub.c)
# 该命令可以查找某个路径下所有源文件，并指定变量名,可以重复此操作添加多个目录下的源文件
# aux_source_directory(/home/xiaohua/cmakeDir SRC)
file(GLOB SRC ${CMAKE_CURRENT_SOURCE_DIR}/src/*.cpp) # CMAKE_CURRENT_SOURCE_DIR为当前CMakeLists所在目录

# PROJECT_SOURCE_DIR 为执行Cmake时，后面所跟的文件目录
# 增加-std=c++11
set(CMAKE_CXX_STANDARD 11)

# 增加-std=c++14
# set(CMAKE_CXX_STANDARD 14)
# 增加-std=c++17
# set(CMAKE_CXX_STANDARD 17)

# 指定头文件路径
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

# 设置路径
# set(HOME /home/xiaohua/cmakeDir)
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/bin)

# 指定库路径
link_directories(${CMAKE_SOURCE_DIR}/lib)

# 链接静态库
# link_libraries(libcalc.a)

# 设置链接库生成路径
set(LIBRARY_OUTPUT_PATH ${CMAKE_CURRENT_SOURCE_DIR}/lib)

# 生成链接库
# add_library(calc SHARED ${SRC}) #动态库
# add_library(calc STATIC ${SRC}) # 静态库

# 设置可执行文件名，与源文件路径
add_executable(app2 ${SRC})

# 链接动态库
target_link_libraries(app2 pthread calc)

# 输出一般日志信息
message(STATUS "source path: ${PROJECT_SOURCE_DIR}")

# 输出警告信息
message(WARNING "source path: ${PROJECT_SOURCE_DIR}")

# # 输出错误信息
# message(FATAL_ERROR "source path: ${PROJECT_SOURCE_DIR}")
