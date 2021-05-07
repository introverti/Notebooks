cmake_minimum_required(VERSION 2.8)
project(project name)

#添加C++11
set(CMAKE_CXX_FLAGS "-std=c++11")
#使用最新的ceres库需要C++14 -o3
set(CMAKE_CXX_FLAGS "-std=c++14 -O3")

#Eiegn库默认安装地址
include_directories("/usr/include/eigen3")

# Pangolin
find_package( Pangolin REQUIRED )
include_directories( ${Pangolin_INCLUDE_DIRS} )
target_link_libraries(xxx ${Pangolin_LIBRARIES} )

# Ceres
find_package(Ceres REQUIRED)
include_directories(${CERES_INCLUDE_DIRS})
target_link_libraries(xxx ${CERES_LIBRARIES})

# g2o
find_package(G2O REQUIRED)
include_directories(${G2O_INCLUDE_DIRS})
target_link_libraries(xxx ${G2O_STUFF_LIBRARY})


# sophus
find_package(Sophus REQUIRED)
include_directories(${Sophus_INCLUDE_DIRS})
# 新版本的Sophus不需要链接外部库 但老版本的要
target_link_libraries(xxx Sophus::Sophus)


# OpenCV
find_package(OpenCV REQUIRED)
include_directories (${OpenCV_INCLUDE_DIRS})
target_link_libraries(xxx ${OpenCV_LIBS})


# yaml-cpp
find_package(yaml-cpp REQUIRED)
include_directories(${YAML_CPP_INCLUDE_DIR})
target_link_libraries(xxx yaml-cpp)

#设置编译模式 Debug
set ( CMAKE_BUILD_TYPE "Debug")

#添加可编译文件
add_executable(xxx xxx.cpp)


#添加子工程
add_subdirectory(xxx)
