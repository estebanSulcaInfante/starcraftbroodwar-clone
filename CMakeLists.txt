﻿cmake_minimum_required(VERSION 3.13)
project(demo2)

# Archivos del Projecto
set(PROJECT_SOURCE
        main.cpp
    )

# C++ Standard se sugiere 11 o 14
set(CMAKE_CXX_STANDARD 14)

message(STATUS ${CMAKE_SOURCE_DIR})
set(SFML_ROOT "${CMAKE_SOURCE_DIR}/64bit/SFML-2.5.1/SFML-2.5.1/SFML-2.5.1/SFML-2.5.1")

set(SFML_INCLUDE_DIR "${SFML_ROOT}/include")
set(SFML_LIBRARY_DIR "${SFML_ROOT}/lib")

if (APPLE)
    set(SFML_DIR "${SFML_ROOT}/Frameworks/SFML.framework/Resources/CMake")
else()
    set(SFML_DIR "${SFML_ROOT}/lib/CMake/SFML")
endif()

link_directories(${SFML_LIBRARY_DIR})
include_directories(${SFML_INCLUDE_DIR})

# Instrucciones para generar el ejecutable
add_executable(${PROJECT_NAME} ${PROJECT_SOURCE})

find_package(SFML 2.5.1
        COMPONENTS
            system
            window
            graphics
            audio
        REQUIRED)

target_link_libraries (${PROJECT_NAME}
        sfml-system
        sfml-window
        sfml-graphics
        sfml-audio
        )
