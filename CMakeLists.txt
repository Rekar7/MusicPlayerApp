cmake_minimum_required(VERSION 3.31)
project(MusicPlayerApp)

set(CMAKE_CXX_STANDARD 17)

find_package(Vulkan REQUIRED)
find_package(glfw3 REQUIRED)

set(IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR}/Imgui)

set(IMGUI_SOURCES
        ${IMGUI_DIR}/imgui.cpp
        ${IMGUI_DIR}/imgui_demo.cpp
        ${IMGUI_DIR}/imgui_draw.cpp
        ${IMGUI_DIR}/imgui_tables.cpp
        ${IMGUI_DIR}/imgui_widgets.cpp
)

SET(IMGUI_BACKEND_SOURCES
        ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
        ${IMGUI_DIR}/backends/imgui_impl_vulkan.cpp
)

add_executable(MusicPlayerApp main.cpp
    ${IMGUI_SOURCES}
        ${IMGUI_BACKEND_SOURCES}
)

target_include_directories(MusicPlayerApp PRIVATE
        ${IMGUI_DIR}
        ${IMGUI_DIR}/backends
)

target_link_libraries(MusicPlayerApp PRIVATE
    Vulkan::Vulkan
        glfw
)
