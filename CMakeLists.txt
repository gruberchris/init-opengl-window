cmake_minimum_required (VERSION 3.6)
project (init-opengl-window)

set(CMAKE_CXX_STANDARD 20)

set(CMAKE_VERBOSE_MAKEFILE 1)
set(APP_VERSION_MAJOR 1)
set(APP_VERSION_MINOR 0)

find_package(OpenGL REQUIRED)

set(MY_HEADER_FILES
        # put all your .h here. Right now we have none.
        # Example :
        # ../common/shader.hpp
        )

set(MY_SOURCE_FILES
        src/main.cpp
        )


add_definitions(-DGLEW_STATIC)

include_directories(
        $ENV{GLFW_INCLUDE_DIRS}
        $ENV{GLEW_INCLUDE_DIRS}
        $ENV{GLM_INCLUDE_DIRS}
)

add_executable(init-opengl-window
        ${MY_HEADER_FILES}
        ${MY_SOURCE_FILES}
        )

target_link_libraries(init-opengl-window
        ${OPENGL_LIBRARY} # filled by "find_package(OpenGL REQUIRED)"
        $ENV{GLFW_LIBRARIES}/glfw3.lib
        $ENV{GLEW_LIBRARIES}/glew32s.lib
        )