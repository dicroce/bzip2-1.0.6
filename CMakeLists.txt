cmake_minimum_required (VERSION 2.8.12)

if(NOT CMAKE_BUILD_TYPE)
    set (CMAKE_BUILD_TYPE Debug)
endif()

add_library (bzip2 bzlib.h
                   bzlib_private.h
                   blocksort.c
                   huffman.c
                   crctable.c
                   randtable.c
                   compress.c
                   decompress.c
                   bzlib.c)

if(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(bzip2 PUBLIC "-O0")
    target_compile_options(bzip2 PUBLIC "-ggdb")
else(CMAKE_BUILD_TYPE STREQUAL "Debug")
    target_compile_options(bzip2 PUBLIC "-O3")
endif(CMAKE_BUILD_TYPE STREQUAL "Debug")
