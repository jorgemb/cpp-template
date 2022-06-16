cmake_minimum_required (VERSION 3.16)

# Add vcpkg
set(CMAKE_TOOLCHAIN_FILE ${CMAKE_CURRENT_SOURCE_DIR}/vcpkg/scripts/buildsystems/vcpkg.cmake
        CACHE STRING "Vcpkg toolchain file")

project ("cpp-template")
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED on)

# Add packages
find_package(fmt REQUIRED CONFIG)

add_executable(main main.cpp)
target_link_libraries(main PRIVATE fmt::fmt)