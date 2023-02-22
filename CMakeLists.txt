cmake_minimum_required (VERSION 3.16)

# Add vcpkg - Allow for global VCPKG installation
if(DEFINED ENV{VCPKG_ROOT})
    message("Using global VCPKG at: " $ENV{VCPKG_ROOT})
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake"
            CACHE STRING "Vcpkg toolchain file")
else()
    message("Using VCPKG in manifest mode")
    set(CMAKE_TOOLCHAIN_FILE "${CMAKE_CURRENT_SOURCE_DIR}/third-party/vcpkg/scripts/buildsystems/vcpkg.cmake"
            CACHE STRING "Vcpkg toolchain file")
endif()

project ("<project-name>")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED on)

# Add packages
find_package(fmt REQUIRED CONFIG)

add_executable(main main.cpp)
target_link_libraries(main PRIVATE fmt::fmt)