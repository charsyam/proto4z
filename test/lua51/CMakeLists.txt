cmake_minimum_required(VERSION 2.6)
project(lua51)

include_directories(../../luasrc/)
include_directories(./)
aux_source_directory(./ source) 
aux_source_directory(../../luasrc/ luasrc) 
set(EXECUTABLE_OUTPUT_PATH ${PROTO4Z_BIN_OUT_PATH})


if (CMAKE_BUILD_TYPE STREQUAL "Debug")
        add_definitions(-Wall -g -ggdb -O0  -D_GLIBCXX_USE_NANOSLEEP)
else()
        add_definitions(-Wall  -O2 -DNDEBUG  -D_GLIBCXX_USE_NANOSLEEP)
endif()
set(CMAKE_CXX_FLAGS -std=c++11)

add_executable(lua51 ${source} ${luasrc})

if(APPLE)
        target_link_libraries(lua51  pthread  m)
else()
        target_link_libraries(lua51  pthread  rt m)
endif()





