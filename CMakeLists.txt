
cmake_minimum_required(VERSION 3.16)
project("oz-dwm" VERSION 0.2.0)

# Config ======================================================================

set(CMAKE_C_STANDARD 99)
set(C_STANDARD_REQUIRED ON)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)

set(CPPFLAGS 
    "-D_DEFAULT_SOURCE"
    "-D_BSD_SOURCE"
    "-D_XOPEN_SOURCE=700L"
    "-DVERSION=\""
    ${VERSION}
    "\""
    ${XINERAMAFLAGS})

set(CFLAGS 
    "-std=c99"
    "-pedantic"
    "-Wall"
    "-Wno-deprecated-declarations"
    "-Os"
    ${CPPFLAGS}
)

set(CMAKE_C_FLAGS_DEBUG "-O0 -g -ggdb -Wall")
set(CMAKE_C_FLAGS_RELEASE "-fstack-protector -s")

# Build ===============================================================

add_executable(dwm)

#Required packages
find_package(X11 REQUIRED)
find_package(Freetype REQUIRED)

target_link_libraries(dwm ${X11_LIBRARIES} ${FREETYPE_LIBRARIES} X11::Xft)
include_directories(${X11_INCLUDE_DIR} ${FREETYPE_INCLUDE_DIRS})

add_compile_definitions(
    VERSION="${CMAKE_PROJECT_VERSION}"
)

#Sources
target_sources(dwm PRIVATE
    src/config.h
    src/drw.h
    src/drw.c
    src/dwm.h
    src/dwm.c
    src/util.h
    src/util.c
    #src/gaps.c
)

install(TARGETS dwm DESTINATION /usr/local/bin)
install(FILES res/wallpaper.png DESTINATION /home/james/ RENAME .ozWallpaper)
