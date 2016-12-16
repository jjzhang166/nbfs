#  Copyright (c) 2016, https://github.com/nebula-im
#  All rights reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

cmake_minimum_required(VERSION 2.6)

project(nbfs C CXX)

set(CMAKE_BUILD_TYPE "Debug")

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    set(CXX_FLAGS -std=c++1y
                  -g
                  -Wall
                  -Wno-unused)
    string(REPLACE ";" " " CMAKE_CXX_FLAGS "${CXX_FLAGS}")
elseif(CMAKE_BUILD_TYPE STREQUAL "Release")
    set(CXX_FLAGS -std=c++1y
                  -O2)
    string(REPLACE ";" " " CMAKE_CXX_FLAGS "${CXX_FLAGS}")
endif()

if(APPLE)
    set(CMAKE_CXX_COMPILER "clang++")
elseif(UNIX)
    set(CMAKE_CXX_COMPILER "g++")
endif()


message(STATUS "build type     =" ${CMAKE_BUILD_TYPE})
message(STATUS "build compiler =" ${CMAKE_CXX_COMPILER})
message(STATUS "build flags    =" ${CMAKE_CXX_FLAGS})

# Executables ---------- runtime targets
# Static libraries ----- archive targets
# Module libraries ----- library targets        模块lib
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/archine)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/lib)

# 利用find_package实现对于依赖包的安装处理


# 利用include_directories索引对应的头文件
#include_directories()

# 利用link_directories连接的目录
#link_directories()

# 完成对于lib的编译
#add_subdirectory()


set(SRC_LIST
        nbfs_server.cc
        nbfs_server.h
)

add_executable(nbfs_server ${SRC_LIST})
#target_link_libraries(nbfs_server nbfs_directory nbfs_store)
target_link_libraries(nbfs_server)


