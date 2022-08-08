cmake_minimum_required(VERSION 3.23)
project(beebem VERSION 0.0.13)

option(BEEBEM_WITH_DEBUGGER "compile with additional logging" OFF)
# TODO: Unix only
option(BEEBEM_WITH_ECONET "compile with econet" ON)
option(BEEBEM_DISABLE_REALTIME_SLIDER "compile without realtime slider on slide bar" ON)
option(BEEBEM_DISABLE_WELCOME_MESSAGE "compile without welcome message" OFF)
option(BEEBEM_ENABLE_FULLSCREEN_FPS "enable full screen FPS indicator" OFF)
option(BEEBEM_ENABLE_SYSTEM_CP "use system cp instead of C file copy" OFF)
option(BEEBEM_ENABLE_FORCE_COLORMAP "force colormap for 8-bit displays" OFF)

if (BEEBEM_WITH_DEBUGGER)
  message(STATUS "enabling debugger")
  add_definitions(-DWITH_DEBUG_OUTPUT=1 -DEG_DEBUG=1)
else()
  message(STATUS "disabling debugger")
  add_definitions(-DWITHOUT_LEVEL_INDICATOR=1, -DWITHOUT_SHENANIGANS=1)
endif()

add_definitions(-DWITH_UNIX_EXTRAS=1 -DREG_FILENAME=beebem.registry)

include(CheckIncludeFile)
CHECK_INCLUDE_FILE("inttypes.h" HAVE_INTTYPES_H)
CHECK_INCLUDE_FILE("stdint.h" HAVE_STDINT_H)
CHECK_INCLUDE_FILE("stdio.h" HAVE_STDIO_H)
CHECK_INCLUDE_FILE("stdlib.h" HAVE_STDLIB_H)
CHECK_INCLUDE_FILE("strings.h" HAVE_STRINGS_H)
CHECK_INCLUDE_FILE("string.h" HAVE_STRING_H)
CHECK_INCLUDE_FILE("sys/stat.h" HAVE_SYS_STAT_H)
CHECK_INCLUDE_FILE("sys/types.h" HAVE_SYS_TYPES_H)
CHECK_INCLUDE_FILE("unistd.h" HAVE_UNISTD_H)

find_package(ZLIB)
set(HAVE_LIBZ ZLIB_FOUND)
if (ZLIB_FOUND)
  set(HAVE_ZLIB_H 1)
endif()

find_package(SDL REQUIRED)

find_package(GTK2 REQUIRED)
message(STATUS "found GTK2 version ${GTK2_VERSION}")
include_directories(${GTK2_INCLUDE_DIRS})

configure_file(config.h.in config.h @ONLY)
add_definitions(-DHAVE_CONFIG_H)

add_subdirectory(src)
add_subdirectory(data)
add_subdirectory(doc)
