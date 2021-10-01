
add_library(lv_driver_sdl STATIC sdl/sdl.c sdl/sdl_gpu.c)

target_compile_definitions(lv_driver_sdl PRIVATE SDL_INCLUDE_PATH=<SDL2/SDL.h> LV_CONF_INCLUDE_SIMPLE)
target_link_libraries(lv_driver_sdl PRIVATE SDL2)
target_link_libraries(lv_driver_sdl PUBLIC lvgl)
target_include_directories(lv_driver_sdl PUBLIC ${LVGL_CONFIG_DIR})
