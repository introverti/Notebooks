cmake_minimum_required(VERSION 2.8)
project(project name)

#添加C++11
set(CMAKE_CXX_FLAGS "-std=c++11")

#Eiegn库默认安装地址
include_directories("/usr/include/eigen3")

# 添加Pangolin依赖
find_package( Pangolin REQUIRED )
include_directories( ${Pangolin_INCLUDE_DIRS} )
#链接外部库到程序
target_link_libraries(xxx ${Pangolin_LIBRARIES} )



# 为使用 sophus，需要使用find_package命令找到它
find_package(Sophus REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})
#新版本的Sophus不需要链接外部库 但老版本的要
target_link_libraries(xxx Sophus::Sophus)


#OpenCV
find_package(OpenCV REQUIRED)
include_directories (${OpenCV_INCLUDE_DIRS})
#可以一次新链接多个外部库
target_link_libraries(xxx ${OpenCV_LIBS} ${Pangolin_LIBRARIES})


#yaml-cpp
find_package(yaml-cpp REQUIRED)
include_directories(${YAML_CPP_INCLUDE_DIR})
target_link_libraries(node_name yaml-cpp)

#设置编译模式 Debug
set ( CMAKE_BUILD_TYPE "Debug")

#添加可编译文件
add_executable(xxx xxx.cpp)


#添加子工程
add_subdirectory(xxx)
