cmake_minimum_required(VERSION 3.18)

project(
    ECP
    VERSION 1.0
    DESCRIPTION "eCP algorithm C++ implementation"
    LANGUAGES CXX)

# Must be in main file
enable_testing()

# The compiled library code, executable code, external libs and tests
add_subdirectory(src)
add_subdirectory(app)
add_subdirectory(extern)
add_subdirectory(tests)

# Setting build flags
list(APPEND flags "-fPIC" "-Wall")
if(NOT WIN32)
  list(APPEND flags "-Wextra" "-Wpedantic")
endif()

target_compile_options(main
    PUBLIC
        ${flags}
        -O3
        -g
)