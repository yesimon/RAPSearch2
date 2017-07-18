cmake_minimum_required (VERSION 3.0.2)
project (rapsearch
         VERSION 2.24.1
         LANGUAGES CXX)

add_definitions(-DPROJECT_VERSION="${PROJECT_VERSION}")
add_subdirectory (Src)
