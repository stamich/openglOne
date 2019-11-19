cmake_minimum_required(VERSION 3.14)
project(openglOne)

set(CMAKE_CXX_STANDARD 17)

add_executable(openglOne main.cpp)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${CMAKE_CURRENT_SOURCE_DIR}/bin")

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14 -pthread -fpermissive")

find_package (PkgConfig REQUIRED)
find_package (OpenGL REQUIRED)
find_package (GLUT REQUIRED)


include_directories(${OPENGL_INCLUDE_DIR}  ${GLUT_INCLUDE_DIRS})

file(GLOB SOURCE_FILES
        *.cpp
        *.h
        )

add_executable(main.cpp include/glad/glad.h glad.c ${SOURCE_FILES})
#
#find_package(glfw3 3.2 REQUIRED)
#pkg_search_module(GLFW REQUIRED glfw3)
#include_directories(${GLFW_INCLUDE_DIRS})
#
#include_directories(${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/GLEW/include/GL)
#link_directories(${CMAKE_CURRENT_SOURCE_DIR}/Dependencies/GLEW/libs)

target_link_libraries (${PROJECT_NAME} ${OPENGL_LIBRARIES} ${GLUT_LIBRARIES} ${GLFW_LIBRARIES} GL m dl Xinerama Xrandr Xi Xcursor X11 Xxf86vm pthread)
