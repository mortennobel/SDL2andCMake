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
include_directories(${SDL2_INCLUDE_DIR})
IF(APPLE)
   INCLUDE_DIRECTORIES ( /System/Library/Frameworks )
   FIND_LIBRARY(OpenGL_LIBRARY OpenGL )
      MARK_AS_ADVANCED (OpenGL_LIBRARY)
      SET(EXTRA_LIBS ${OpenGL_LIBRARY})
ELSE(TRUE)
   find_package(OpenGL REQUIRED)
   include_directories(${OpenGL_INCLUDE_DIRS})
   SET(EXTRA_LIBS ${OPENGL_LIBRARY})
ENDIF (APPLE)

target_link_libraries(${PROJECT_NAME} ${EXTRA_LIBS} ${SDL2_LIBRARY} )

