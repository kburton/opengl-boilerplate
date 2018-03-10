cmake_minimum_required(VERSION 2.8)

find_package(OpenGL REQUIRED)

set(GLFW_SOURCE_DIR "external/glfw")
set(GLEW_SOURCE_DIR "external/glew")
set(LINMATH_SOURCE_DIR "external/linmath.h")

# GLFW-specific configuration
set(BUILD_SHARED_LIBS OFF CACHE BOOL "")
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "")
set(GLFW_BUILD_TESTS OFF CACHE BOOL "")
set(GLFW_BUILD_DOCS OFF CACHE BOOL "")
set(GLFW_INSTALL OFF CACHE BOOL "")

add_subdirectory(${GLFW_SOURCE_DIR} ${GLEW_SOURCE_DIR})

include_directories(${GLFW_SOURCE_DIR}/include
                    ${GLFW_SOURCE_DIR}/deps
                    ${GLEW_SOURCE_DIR}/include
                    ${LINMATH_SOURCE_DIR})

add_library(glew STATIC
  ${GLEW_SOURCE_DIR}/src/glew.c
  ${GLEW_SOURCE_DIR}/include
)

target_link_libraries(glew ${GLFW_LIBRARIES})

add_definitions(
  -DGLEW_STATIC
)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS}")
SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/out)

file(GLOB SOURCE_FILES src/**.c)

if (APPLE)
    set(APP_NAME "OpenGLBoilerplate")

    if (EXISTS ${CMAKE_CURRENT_SOURCE_DIR}/icon.icns)
        add_executable(${APP_NAME} MACOSX_BUNDLE main.cpp icon.icns)
        set_source_files_properties("icon.icns" PROPERTIES MACOSX_PACKAGE_LOCATION "Resources")
        set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_ICON_FILE ${CMAKE_CURRENT_SOURCE_DIR}/icon.icns)
    else ()

        add_executable(${APP_NAME} MACOSX_BUNDLE ${SOURCE_FILES})
    endif ()

#    set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_INFO_PLIST ${CMAKE_CURRENT_SOURCE_DIR}/app.plist.in)

    set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_BUNDLE_NAME ${APP_NAME})
    set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_SHORT_VERSION_STRING "1.0")
    set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_LONG_VERSION_STRING "1.0")
    set_target_properties(${APP_NAME} PROPERTIES MACOSX_BUNDLE_INFO_STRING "OpenGL boilerplate example app")

    set(EXECUTABLE_NAME ${APP_NAME})
else()
    set(EXECUTABLE_NAME "opengl-boilerplate")
    add_executable(${EXECUTABLE_NAME} ${SOURCE_FILES})
endif()

target_link_libraries(${EXECUTABLE_NAME} glfw ${GLFW_LIBRARIES} glew ${OPENGL_LIBRARIES})

# Visual Studio-specific properties
set_property(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR} PROPERTY VS_STARTUP_PROJECT ${EXECUTABLE_NAME})

set(LICENSES_TXT "${EXECUTABLE_OUTPUT_PATH}/LICENSES.txt")

function(add_license NAME IN_FILE)
  file(READ ${IN_FILE} CONTENTS)
  file(APPEND ${LICENSES_TXT} "*****  ${NAME}  *****\n\n${CONTENTS}\n\n")
endfunction()

file(REMOVE ${LICENSES_TXT})

add_license("GLEW" "external/glew/LICENSE.txt")
add_license("GLFW" "external/glfw/LICENSE.md")
