cmake_minimum_required(VERSION 3.22)

project(multifitting LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt5 REQUIRED COMPONENTS Widgets PrintSupport)
#qt_standard_project_setup()
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

file(GLOB_RECURSE SRC_FILES "*.c" "*.cpp" "*.cc")

add_executable(multifitting ${SRC_FILES})

target_include_directories(multifitting PRIVATE 3rdparty 3rdparty/RandomOps 3rdparty/SwarmOps 3rdparty/Faddeeva 3rdparty/QCustomPlot .)

target_link_libraries(multifitting PRIVATE Qt5::Widgets Qt5::PrintSupport)
target_link_libraries(multifitting PRIVATE gsl gslcblas)

target_compile_options(multifitting PRIVATE -Wno-everything)
