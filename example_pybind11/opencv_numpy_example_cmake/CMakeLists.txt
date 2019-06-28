cmake_minimum_required(VERSION 2.8.12)
project(opencv_numpy_example)



 # find OpenCV
 find_package(OpenCV REQUIRED)
 message(STATUS "OpenCV library status:")
 message(STATUS "    version: ${OpenCV_VERSION}")
 #message(STATUS "    libraries: ${OpenCV_LIBS}")
 message(STATUS "    libraries: ${OpenCV_LIBRARIES}")
 message(STATUS "    include path: ${OpenCV_INCLUDE_DIRS}")

 if(CMAKE_VERSION VERSION_LESS "3.8.11")
     # Add OpenCV headers location to your include paths
     include_directories(${OpenCV_INCLUDE_DIRS})
 endif()

#link_libraries(opencv_numpy_example ${OpenCV_LIBRARIES})

add_subdirectory(pybind11)
pybind11_add_module(opencv_numpy_example src/main.cpp)

## NOTICE ** PRIVATE ** must added
target_link_libraries(opencv_numpy_example PRIVATE ${OpenCV_LIBRARIES})
#target_link_libraries(opencv_numpy_example ${OpenCV_LIBRARIES})
#target_link_libraries(opencv_numpy_example ${OpenCV_LIBS})
