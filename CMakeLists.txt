cmake_minimum_required(VERSION 3.13)
project(SDLPlayground)

find_package(SDL2 REQUIRED)


# Group SDL2 properties into a single target
add_library(sdl2_interface INTERFACE)
target_link_libraries(
    sdl2_interface INTERFACE ${SDL2_INCLUDE_DIRS}
)
target_include_directories(
    sdl2_interface INTERFACE ${SDL2_LIBRARIES}
)


add_executable(sdl_playground)
target_compile_features(sdl_playground PRIVATE c_std_11)
target_include_directories(sdl_playground PRIVATE src)
target_link_libraries(sdl_playground PRIVATE sdl2_interface)
target_sources(
    sdl_playground 

    PRIVATE 
    src/game.h
    src/game.c
    src/main.c
)
