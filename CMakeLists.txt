cmake_minimum_required( VERSION 2.8 )

## Load CMAKE configuration from environment variables
set( CMAKE_MODULE_PATH $ENV{CMAKE_MODULE_PATH} )
set( CMAKE_PREFIX_PATH $ENV{CMAKE_PREFIX_PATH} )

## Specify a project name
#if (NOT PROJECT_NAME)
project( toro )
#endif(NOT PROJECT_NAME)

## Required software
#find_package( <<<name>>> REQUIRED )

## C++ compiler options
set( CMAKE_CXX_FLAGS "-Wall -Wextra" )
set( CMAKE_CXX_FLAGS_DEBUG "-g -O0" )
set( CMAKE_CXX_FLAGS_RELEASE "-O3" )

## Set the build type
if( NOT CMAKE_BUILD_TYPE )
  set( CMAKE_BUILD_TYPE "Debug"
       CACHE STRING "Build configuration 'Release' or 'Debug'."
       FORCE )
endif()

## Sources and headers
include_directories( ${CMAKE_CURRENT_SOURCE_DIR}/include )

## Find all source files to be compiled into object files
add_library(toro-shared SHARED
  src/posegraph2.cpp
  src/treeoptimizer2.cpp
  src/toro.cpp
)
set_target_properties(toro-shared PROPERTIES OUTPUT_NAME toro)

add_library(toro-static STATIC
  src/posegraph2.cpp
  src/treeoptimizer2.cpp
  src/toro.cpp
)
set_target_properties(toro-static PROPERTIES OUTPUT_NAME toro)

add_library(toro3d-shared SHARED
  src/posegraph3.cpp
  src/treeoptimizer3.cpp
  src/treeoptimizer3_iteration.cpp
  src/toro.cpp
)
set_target_properties(toro3d-shared PROPERTIES OUTPUT_NAME toro3d)

add_library(toro3d-static STATIC
  src/posegraph3.cpp
  src/treeoptimizer3.cpp
  src/treeoptimizer3_iteration.cpp
  src/toro.cpp
)
set_target_properties(toro3d-static PROPERTIES OUTPUT_NAME toro3d)
