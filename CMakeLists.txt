cmake_minimum_required(VERSION 3.11)
project(libretro
    DESCRIPTION "libretro"
    HOMEPAGE_URL "https://github.com/robloach/libretro-cmake"
    VERSION 0.0.1
    LANGUAGES C
)

# CMake Plugins
include(FetchContent)

# libretro-common
FetchContent_Declare(
    libretro_common_src
    GIT_REPOSITORY https://github.com/libretro/libretro-common.git
    GIT_TAG b0c348ea5543c4d7fb0bc479258aa6988b20c0c9
)
FetchContent_MakeAvailable(libretro_common_src)
FetchContent_GetProperties(libretro_common_src)

add_library(${PROJECT_NAME} INTERFACE)
target_include_directories(${PROJECT_NAME} INTERFACE ${libretro_common_src_SOURCE_DIR}/include)
target_compile_definitions(${PROJECT_NAME} INTERFACE __LIBRETRO__)

# Examples
add_subdirectory(examples)