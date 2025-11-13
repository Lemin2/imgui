# Template CMakeLists.txt for ESP-IDF Dear ImGui component
# If you copy this repo template as-is, this file will be committed.
# The workflow also regenerates an equivalent file during sync.

idf_component_register(
    SRCS
        imgui.cpp
        imgui_draw.cpp
        imgui_tables.cpp
        imgui_widgets.cpp
    INCLUDE_DIRS
        .
)

# Optionally include demo (if file exists)
if(EXISTS "${CMAKE_CURRENT_LIST_DIR}/imgui_demo.cpp")
    target_sources(${COMPONENT_LIB} PRIVATE imgui_demo.cpp)
endif()

target_compile_definitions(${COMPONENT_LIB} PUBLIC IMGUI_DISABLE_OBSOLETE_FUNCTIONS=1)
