cmake_minimum_required(VERSION 3.2)
project(SDL2andCMake)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake")

set(SOURCE_FILES main.cpp)

add_executable(SDL2andCMake ${SOURCE_FILES})

find_package(SDL2 REQUIRED)
find_package(SDL2_Image REQUIRED)

include_directories(${SDL2_INCLUDE_DIR}
                    ${SDL2_IMAGE_INCLUDE_DIR})
target_link_libraries(${PROJECT_NAME}  ${SDL2_LIBRARY}
                             ${SDL2_IMAGE_LIBRARIES})

