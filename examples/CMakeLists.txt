
add_library(libretro_rendering SHARED libretro_rendering.c)
target_link_libraries(libretro_rendering PUBLIC libretro)
set_target_properties(libretro_rendering PROPERTIES
    PREFIX ""
    C_STANDARD 11
)

# Strict Warnings and Errors
if(MSVC)
    target_compile_options(libretro_rendering PRIVATE /W4 /WX)
else()
    target_compile_options(libretro_rendering PRIVATE -Wall -Wextra -Wpedantic -Werror)
endif()