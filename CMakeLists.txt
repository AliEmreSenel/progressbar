project(ProgressBar)

cmake_minimum_required(VERSION 3.0)

set(CURSES_NEED_NCURSES TRUE)
find_package(Curses)
include_directories(${CURSES_INCLUDE_DIRS})

add_library(progressbar progressbar.c)
add_library(statusbar statusbar.c)

set_target_properties(progressbar PROPERTIES PUBLIC_HEADER
    ${PROJECT_SOURCE_DIR}/progressbar.h)
set_target_properties(statusbar PROPERTIES PUBLIC_HEADER
    ${PROJECT_SOURCE_DIR}/statusbar.h)
