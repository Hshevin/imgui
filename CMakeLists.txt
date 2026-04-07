cmake_minimum_required(VERSION 3.16)
project(ImGui)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_library(ImGui STATIC
            imgui_demo.cpp
            imgui_draw.cpp
            imgui_tables.cpp
            imgui_widgets.cpp
            imgui.cpp
            backends/imgui_impl_glfw.cpp
            backends/imgui_impl_opengl3.cpp
            )

target_include_directories(ImGui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})
target_include_directories(ImGui PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/backends)

# imgui_impl_glfw 需要链接 GLFW
target_link_libraries(ImGui PUBLIC glfw)

# imgui_impl_opengl3 需要链接 OpenGL (通过 glad)
target_link_libraries(ImGui PUBLIC glad)