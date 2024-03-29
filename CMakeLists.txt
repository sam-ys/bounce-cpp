cmake_minimum_required (VERSION 3.0)
project(bounce)
set(MY_APP_NAME bounce)

#
##
### Compilation and output
#####################################################################################
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -W")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pedantic")

string(TOLOWER ${CMAKE_BUILD_TYPE} MY_BUILD_TYPE)

if (MY_BUILD_TYPE STREQUAL "debug")
  set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS} -g")
  set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS} -O0")
endif (MY_BUILD_TYPE STREQUAL "debug")

if (MY_BUILD_TYPE STREQUAL "release")
  set(CMAKE_C_FLAGS "${CMAKE_CXX_FLAGS} -O3")
endif (MY_BUILD_TYPE STREQUAL "release")

file(GLOB SRCS *.cpp)
#####################################################################################
###
##
#

add_executable(${MY_APP_NAME} ${SRCS})

target_link_libraries(${MY_APP_NAME} LINK_PUBLIC SDL2main)
target_link_libraries(${MY_APP_NAME} LINK_PUBLIC SDL2)
target_link_libraries(${MY_APP_NAME} LINK_PUBLIC GL)
target_link_libraries(${MY_APP_NAME} LINK_PUBLIC GLU)
