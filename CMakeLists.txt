cmake_minimum_required(VERSION 3.2)
project(SDL2andCMake)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")

set(SOURCE_FILES main.cpp)

add_executable(SDL2andCMake ${SOURCE_FILES})

find_package(SDL2 REQUIRED)
#########################################################
# FIND OPENGL
#########################################################
find_package(OpenGL REQUIRED)
include_directories(${OpenGL_INCLUDE_DIRS})
link_directories(${OpenGL_LIBRARY_DIRS})
add_definitions(${OpenGL_DEFINITIONS})
if(NOT OPENGL_FOUND)
    message(ERROR " OPENGL not found!")
endif(NOT OPENGL_FOUND)

include_directories(${SDL2_INCLUDE_DIR})

target_link_libraries(${PROJECT_NAME}  ${SDL2_LIBRARY} ${OpenGL_LIBRARY_DIRS})

