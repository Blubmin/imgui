# ImGui Lib
add_library(imgui
  imconfig.h
  imgui_demo.cpp
  imgui_draw.cpp
  imgui_internal.h
  imgui_widgets.cpp
  imgui.cpp
  imgui.h
  imstb_rectpack.h
  imstb_textedit.h
  imstb_truetype.h
)


# GLFW Binding
add_library(imgui_glfw_opengl3
  examples/imgui_impl_glfw.h
  examples/imgui_impl_glfw.cpp
  examples/imgui_impl_opengl3.cpp
  examples/imgui_impl_opengl3.h
)
target_link_libraries(imgui_glfw_opengl3
  ${OPENGL_gl_LIBRARY}
  gl3w
  glfw
  imgui
)

# ImGui Example App
include_directories(${CMAKE_CURRENT_SOURCE_DIR})
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/examples)
add_definitions(-DIMGUI_IMPL_OPENGL_LOADER_GL3W)
add_executable(imgui_opengl3_example
  examples/example_glfw_opengl3/main.cpp
)
target_link_libraries(imgui_opengl3_example
  imgui
  imgui_glfw_opengl3
)
