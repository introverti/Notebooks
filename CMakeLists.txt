cmake_minimum_required(VERSION 2.8)
project(project name)

#添加C++11
set(CMAKE_CXX_FLAGS "-std=c++11")

#Eiegn库默认安装地址
include_directories("/usr/include/eigen3")

# 添加Pangolin依赖
find_package( Pangolin REQUIRED )
include_directories( ${Pangolin_INCLUDE_DIRS} )

# 为使用 sophus，需要使用find_package命令找到它
find_package(Sophus REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})

#OpenCV
find_package(OpenCV REQUIRED)
include_directories (${OpenCV_INCLUDE_DIRS})

#设置编译模式 Debug
set ( CMAKE_BUILD_TYPE "Debug")

#添加可编译文件
add_executable(xxx xxx.cpp)

#链接外部库到程序
target_link_libraries(xxx ${Pangolin_LIBRARIES} )

#新版本的Sophus不需要链接外部库 但老版本的要
target_link_libraries(xxx Sophus::Sophus)

#可以一次新链接多个外部库
target_link_libraries(xxx ${OpenCV_LIBS} ${Pangolin_LIBRARIES})

#添加子工程
add_subdirectory(xxx)
