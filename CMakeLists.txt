set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

cmake_minimum_required(VERSION 3.16)

project(testRenderer LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(vendor/glfw)

add_subdirectory(vendor/glad/cmake glad_cmake)

glad_add_library(glad_gl_core_33
    STATIC
    REPRODUCIBLE
    API gl:core=3.3
)

add_executable(testRenderer src/main.cpp)

target_link_libraries(testRenderer PRIVATE
    glfw
    glad_gl_core_33
)
