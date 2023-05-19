cmake_minimum_required(VERSION 3.15)

# Don't allow in-source building
if (CMAKE_BINARY_DIR STREQUAL CMAKE_CURRENT_SOURCE_DIR)
  message(FATAL_ERROR "Building in-source is not supported! Create a build dir and remove ${CMAKE_SOURCE_DIR}/CMakeCache.txt")
endif()

project(lab LANGUAGES CXX VERSION 0.1)

## Set C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

# control where the static and shared libraries are built so that on windows
# we don't need to tinker with the path to run the executable
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}")
set(CMAKE_LIBRARY_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}")
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "${PROJECT_BINARY_DIR}")
set(CMAKE_MODULE_PATH "${PROJECT_SOURCE_DIR}/cmake" ${CMAKE_MODULE_PATH})
set(CMAKE_DEBUG_POSTFIX d)

## Identify debug vs release builds with a postfix
## Add address sanatizers for debug build only!
if (CMAKE_BUILD_TYPE STREQUAL "Debug")
  set(SANITIZE_ADDRESS TRUE)
  find_package(Sanitizers)
endif (CMAKE_BUILD_TYPE STREQUAL "Debug")

## Add the src to the build
add_subdirectory(src)

## Packaging
include(InstallRequiredSystemLibraries)
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/License.txt")
set(CPACK_PACKAGE_VERSION_MAJOR "${lab_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${lab_VERSION_MINOR}")
set(CPACK_SOURCE_GENERATOR "ZIP")
set(CPACK_PACKAGE_NAME "cs117-p4-starter")
set(CPACK_SOURCE_PACKAGE_FILE_NAME "${CPACK_PACKAGE_NAME}")
set(CPACK_SOURCE_IGNORE_FILES
    /.vscode
    /.vagrant
    /.git
    /dist
    /.*build.*
    /\\\\.DS_Store
    solution\.cpp
)
include(CPack)
