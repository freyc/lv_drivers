
add_library(lv_driver_sdl STATIC sdl/sdl.c sdl/sdl_gpu.c)

target_compile_definitions(lv_driver_sdl PRIVATE SDL_INCLUDE_PATH=<SDL2/SDL.h>)
target_link_libraries(lv_driver_sdl PRIVATE SDL2)
