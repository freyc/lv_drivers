
find_package(SDL2 REQUIRED)

add_library(lv_driver_sdl STATIC sdl/sdl.c)

target_compile_definitions(lv_driver_sdl 
    PRIVATE 
        SDL_INCLUDE_PATH=<SDL2/SDL.h> 
        LV_LVGL_H_INCLUDE_SIMPLE
    PUBLIC
        LV_CONF_INCLUDE_SIMPLE
        USE_SDL)

target_include_directories(lv_driver_sdl 
    PUBLIC 
        ${LVGL_CONFIG_DIR} 
        ${SDL2_INCLUDE_DIRS})

target_link_libraries(lv_driver_sdl 
    PRIVATE 
        lvgl
        ${SDL2_LIBRARIES})

#[[
add_library(lv_driver_sdl_gpu STATIC sdl/sdl_gpu.c)
target_compile_definitions(lv_driver_sdl_gpu PRIVATE SDL_INCLUDE_PATH=<SDL2/SDL.h> LV_CONF_INCLUDE_SIMPLE)
target_link_libraries(lv_driver_sdl_gpu PRIVATE ${SDL2_LIBRARIES})
target_link_libraries(lv_driver_sdl_gpu PRIVATE lvgl)
target_include_directories(lv_driver_sdl_gpu PUBLIC ${LVGL_CONFIG_DIR} ${SDL2_INCLUDE_DIRS})
]]

find_package(PkgConfig REQUIRED)
pkg_check_modules(GTK3 REQUIRED gtk+-3.0)

add_library(lv_driver_gtk STATIC gtkdrv/gtkdrv.c)

target_compile_definitions(lv_driver_gtk PRIVATE LV_CONF_INCLUDE_SIMPLE)
target_compile_definitions(lv_driver_gtk PUBLIC USE_GTK)
target_link_libraries(lv_driver_gtk PRIVATE ${GTK3_LIBRARIES})
target_link_libraries(lv_driver_gtk PRIVATE lvgl)
target_include_directories(lv_driver_gtk PUBLIC ${LVGL_CONFIG_DIR} ${GTK3_INCLUDE_DIRS})