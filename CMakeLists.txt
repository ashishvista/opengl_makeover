cmake_minimum_required(VERSION 2.6)
  
project(OPENGLEXAMPLES)

option(BUILD_OGL43 "Bild OpenGL 4.3 examples" OFF)
mark_as_advanced(BUILD_OGL43)

find_package(OpenGL REQUIRED)

set(CURL_LIBRARY "-lcurl")
#sudo apt install libcurl4-openssl-dev
find_package(CURL REQUIRED)

add_subdirectory(libs/glfw)
add_subdirectory(libs/glxw)

include_directories(libs/glfw/include)
include_directories(libs/glm)
include_directories(${CMAKE_BINARY_DIR}/libs/glxw/include)
include_directories(${CURL_INCLUDE_DIR})
include_directories(common)

set(CMAKE_CXX_FLAGS "-O2 -Wall -Wextra")
SET(LIBRARIES ${CURL_LIBRARIES} glfw glxw ${GLFW_LIBRARIES} ${GLXW_LIBRARY} ${OPENGL_LIBRARY} ${CMAKE_DL_LIBS})

link_directories (${OPENGLEXAMPLES_BINARY_DIR}/bin)

add_library (common common/stb_implementation.cpp)
target_link_libraries(common ${LIBRARIES} )

add_executable (makeover_tool makeover_tool/main.cpp)
target_link_libraries(makeover_tool ${LIBRARIES} common )


add_executable (00skeleton 00skeleton.cpp)
target_link_libraries(00skeleton ${LIBRARIES} )

add_executable (01shader_vbo1 01shader_vbo1.cpp)
target_link_libraries(01shader_vbo1 ${LIBRARIES} )

add_executable (01shader_vbo2 01shader_vbo2.cpp)
target_link_libraries(01shader_vbo2 ${LIBRARIES} )

add_executable (02indexed_vbo 02indexed_vbo.cpp)
target_link_libraries(02indexed_vbo ${LIBRARIES} )

add_executable (03texture 03texture.cpp)
target_link_libraries(03texture ${LIBRARIES} )

add_executable (04perspective 04perspective.cpp)
target_link_libraries(04perspective ${LIBRARIES} )

add_executable (05fbo_fxaa 05fbo_fxaa.cpp)
target_link_libraries(05fbo_fxaa ${LIBRARIES} )

add_executable (06instancing1 06instancing1.cpp)
target_link_libraries(06instancing1 ${LIBRARIES} )

add_executable (06instancing2_buffer_texture 06instancing2_buffer_texture.cpp)
target_link_libraries(06instancing2_buffer_texture ${LIBRARIES} )

add_executable (06instancing3_uniform_buffer 06instancing3_uniform_buffer.cpp)
target_link_libraries(06instancing3_uniform_buffer ${LIBRARIES} )

add_executable (07geometry_shader_blending 07geometry_shader_blending.cpp)
target_link_libraries(07geometry_shader_blending ${LIBRARIES} )

add_executable (08map_buffer 08map_buffer.cpp)
target_link_libraries(08map_buffer ${LIBRARIES} )

add_executable (09transform_feedback 09transform_feedback.cpp)
target_link_libraries(09transform_feedback ${LIBRARIES} )

add_executable (10queries_conditional_render 10queries_conditional_render.cpp)
target_link_libraries(10queries_conditional_render ${LIBRARIES} )

add_executable (11tesselation 11tesselation.cpp)
target_link_libraries(11tesselation ${LIBRARIES} )

add_executable (12shader_image_load_store 12shader_image_load_store.cpp)
target_link_libraries(12shader_image_load_store ${LIBRARIES} )

add_executable (13compute_shader_nbody 13compute_shader_nbody.cpp)
target_link_libraries(13compute_shader_nbody ${LIBRARIES} )

