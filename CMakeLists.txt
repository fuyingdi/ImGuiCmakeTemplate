cmake_minimum_required(VERSION 3.0.0)
project(MyTool VERSION 0.0.1)

find_package(OpenGL)

set(CMAKE_CXX_STANDARD 11) 
set(CMAKE_CXX_STANDARD_REQUIRED True) 

set(MYTOOL_SOURCE_DIR ${CMAKE_SOURCE_DIR}/src)
set(IMGUI_SOURCE_DIR ${CMAKE_SOURCE_DIR}/imgui)

set(IMGUI_LIBS_DIR ${IMGUI_SOURCE_DIR}/libs)

set(GL3W_SOURCE_DIR ${IMGUI_LIBS_DIR}/gl3w)
set(GLFW_INCLUDE_DIR ${IMGUI_LIBS_DIR}/glfw/include)
set(GLFW_LIB ${IMGUI_LIBS_DIR}/glfw/lib-vc2010-64/glfw3.lib)

set(SOURCE_FILES
    ${MYTOOL_SOURCE_DIR}/main.cpp

    ${IMGUI_SOURCE_DIR}/imgui_demo.cpp
    ${IMGUI_SOURCE_DIR}/imgui_draw.cpp
    ${IMGUI_SOURCE_DIR}/imgui_tables.cpp
    ${IMGUI_SOURCE_DIR}/imgui.cpp
    ${IMGUI_SOURCE_DIR}/imgui_widgets.cpp

    ${IMGUI_SOURCE_DIR}/backends/imgui_impl_opengl3.cpp
    ${IMGUI_SOURCE_DIR}/backends/imgui_impl_glfw.cpp
)

set(EXECUTABLE_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/out)

add_executable(sample ${SOURCE_FILES})

target_include_directories(sample PRIVATE
    ${MYTOOL_SOURCE_DIR}
    ${IMGUI_SOURCE_DIR}
    ${IMGUI_SOURCE_DIR}/backends
    ${GLFW_INCLUDE_DIR}
    ${GL3W_SOURCE_DIR}
)

target_link_libraries(sample
    OpenGL::GL
    ${GLFW_LIB}
)