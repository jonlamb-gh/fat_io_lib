cmake_minimum_required(VERSION 3.2 FATAL_ERROR)

project(libfatio VERSION 0.1 LANGUAGES C)

add_library(
    fatio
    STATIC
    src/fat_access.c
    src/fat_cache.c
    src/fat_filelib.c
    src/fat_format.c
    src/fat_misc.c
    src/fat_string.c
    src/fat_table.c
    src/fat_write.c)

set_property(
    TARGET
    fatio
    PROPERTY
    C_STANDARD
    99)

target_compile_options(
    fatio
    PRIVATE
    -Wall
    -Wextra
    -Wno-unused-parameter
    -Wwrite-strings
    -Wstrict-prototypes
    -Wmissing-include-dirs
    -Wno-unused-function
    -Werror)

target_include_directories(
    fatio
    PUBLIC
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include>
    $<INSTALL_INTERFACE:include>
    PRIVATE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/include/fat>)

target_link_libraries(
    fatio
    Configuration
    muslc
    utils)
