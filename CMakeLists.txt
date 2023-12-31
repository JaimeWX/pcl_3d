cmake_minimum_required(VERSION 3.14)
project(PCL_3D)
set(CMAKE_CXX_STANDARD 14)

# 设置输出根目录为build/Debug
set(OUTPUT_DIRECTORY_ROOT ${CMAKE_CURRENT_SOURCE_DIR}/build/${CMAKE_BUILD_TYPE})
# 设置可执行程序输出到build/Debug/bin目录
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${OUTPUT_DIRECTORY_ROOT}/bin" CACHE PATH "Runtime directory" FORCE)
# 设置库文件输出到build/Debug/lib目录
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${OUTPUT_DIRECTORY_ROOT}/lib" CACHE PATH "Library directory" FORCE)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${OUTPUT_DIRECTORY_ROOT}/lib" CACHE PATH "Archive directory" FORCE)

find_package(PCL REQUIRED)
# 包含头文件目录
include_directories(${PCL_INCLUDE_DIRS})
# 设置依赖库链接目录
link_directories(${PCL_LIBRARY_DIRS})
# 添加预处理器和编译器标记
add_definitions(${PCL_DEFINITIONS})

add_executable(pcl_demo src/pcl_demo.cpp)
target_link_libraries(pcl_demo ${PCL_LIBRARIES})

add_executable(cloud_viewer src/cloud_viewer.cpp)
target_link_libraries(cloud_viewer ${PCL_LIBRARIES})

add_executable(pcl_visualizer src/pcl_visualizer.cpp)
target_link_libraries(pcl_visualizer ${PCL_LIBRARIES})

add_executable(pcl_transform src/pcl_transform.cpp)
target_link_libraries(pcl_transform ${PCL_LIBRARIES})

add_executable(serialize_pcd src/serialize_pcd.cpp)
target_link_libraries(serialize_pcd ${PCL_LIBRARIES})

add_executable(deserialize_pcd src/deserialize_pcd.cpp)
target_link_libraries(deserialize_pcd ${PCL_LIBRARIES})