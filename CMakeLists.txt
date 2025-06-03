cmake_minimum_required(VERSION 3.5.0)
project(sdl2-testing-parent-folder)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)

set(SourceFiles main.cpp)
cmake_policy(SET CMP0074 NEW)

set(CMAKE_PREFIX_PATH "/usr/lib/x86_64-linux-gnu/cmake/SDL2_image")

# Find packages
find_package(SDL2 REQUIRED)
#find_package(SDL2_image REQUIRED)
#find_package(SDL2_ttf REQUIRED)

# Include directories
include_directories(${SDL2_INCLUDE_DIRS} ${SDL2_IMAGE_INCLUDE_DIRS} ${SDL2_TTF_INCLUDE_DIRS} /home/slice/code-projects/cpp-projects/nea-ik-from-desmos/libs/kiss_sdl/)

# Add kiss_sdl source files
# /home/slice/code-projects/cpp-projects/nea-ik-from-desmos/libs/kiss_sdl
set(KISS_SDL_SOURCES
    /home/slice/code-projects/cpp-projects/nea-ik-from-desmos/libs/kiss_sdl/kiss_draw.c
    /home/slice/code-projects/cpp-projects/nea-ik-from-desmos/libs/kiss_sdl/kiss_widgets.c
    /home/slice/code-projects/cpp-projects/nea-ik-from-desmos/libs/kiss_sdl/kiss_general.c
    /home/slice/code-projects/cpp-projects/nea-ik-from-desmos/libs/kiss_sdl/kiss_posix.c
    #libs/kiss_sdl/kiss_example1.c
    #libs/kiss_sdl/kiss_example2.c
)

#debugging
message(STATUS "SDL2_LIBRARIES: ${SDL2_LIBRARIES}")
message(STATUS "SDL2_IMAGE_LIBRARIES: ${SDL2_IMAGE_LIBRARIES}")
message(STATUS "SDL2_TTF_LIBRARIES: ${SDL2_TTF_LIBRARIES}")

# Add executable
add_executable(${PROJECT_NAME} ${KISS_SDL_SOURCES} src/main.cpp) # ${SourceFiles} was in there too

# Link libraries
#target_link_libraries(${PROJECT_NAME} ${SDL2_LIBRARIES} ${SDL2_IMAGE_LIBRARIES} ${SDL2_TTF_LIBRARIES} kiss_sdl)
target_link_libraries(${PROJECT_NAME}
    SDL2::SDL2
    SDL2::SDL2main
    /usr/lib/x86_64-linux-gnu/libSDL2_image.so
    /usr/lib/x86_64-linux-gnu/libSDL2_ttf.so
)

