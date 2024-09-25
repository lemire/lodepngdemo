cmake_minimum_required(VERSION 3.28)
project(lodedemo)
set(CMAKE_CXX_STANDARD 17)

include(cmake/CPM.cmake)
CPMAddPackage("gh:fmtlib/fmt#11.0.2")
CPMAddPackage("gh:ocornut/imgui@1.91.2")
add_library(imgui STATIC
    ${imgui_SOURCE_DIR}/imgui.cpp
    ${imgui_SOURCE_DIR}/imgui_demo.cpp
    ${imgui_SOURCE_DIR}/imgui_draw.cpp
    ${imgui_SOURCE_DIR}/imgui_widgets.cpp
    ${imgui_SOURCE_DIR}/imgui_tables.cpp
)
target_include_directories(imgui PUBLIC "${imgui_SOURCE_DIR}")
target_include_directories(imgui PUBLIC "${imgui_SOURCE_DIR}/backends")

CPMAddPackage("gh:glfw/glfw#3.4")
CPMAddPackage(
    NAME lodepng
    URL https://github.com/lvandeve/lodepng/archive/ed3c5f14b136c936d615ee3b38aaa7e7e642f12c.zip
)
add_library(lodepng STATIC "${lodepng_SOURCE_DIR}/lodepng.cpp")
target_include_directories(lodepng PUBLIC  "${lodepng_SOURCE_DIR}")

add_executable(main main.cpp)
target_link_libraries(main fmt::fmt-header-only glfw imgui lodepng)