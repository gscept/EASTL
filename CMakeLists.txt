cmake_minimum_required(VERSION 2.6)

project("EASTL" CXX)

# path setting
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)
set(LIBRARY_OUTPUT_PATH ${CMAKE_BINARY_DIR}/lib)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake_module)


# find EASTL
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)
link_directories(${LIBRARY_OUTPUT_PATH})

set(EASTL_SKIP_LIBRARY_FINDING TRUE)
find_package(EASTL REQUIRED)
set(EASTL_LIBRARY EASTL)

add_definitions(${EASTL_DEFINITIONS})
include_directories(${EASTL_INCLUDE_DIR})


# create library
aux_source_directory(${CMAKE_CURRENT_SOURCE_DIR}/src LIB_SRCS)
source_group("eastl" FILES ${LIB_SRCS})
add_library(${PROJECT_NAME} STATIC ${LIB_SRCS})

SET_DEFAULT_OUTPUT(${PROJECT_NAME})