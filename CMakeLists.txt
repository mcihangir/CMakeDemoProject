cmake_minimum_required(VERSION 3.10)
project(CMakeDemoProject)

set(CMAKE_C_STANDARD 11) # -std=c11
set(CMAKE_C_STANDARD_REQUIRED ON)

# Adds options to the compilation of source files.
# NOTE: This is global. Act for all targets in the current directory and below 
# that are added after this command is invoked
option(ENABLE_WARNINGS "Compile with all warnings" ON)

if(ENABLE_WARNINGS)
    if(CMAKE_C_COMPILER_ID MATCHES "GNU"
    OR CMAKE_CXX_COMPILER_ID MATCHES "GNU")
        add_compile_options(-Wall -Wextra)
    elseif(MSVC)
        add_compile_options(/W4)
    endif()
endif()

add_subdirectory(src)


