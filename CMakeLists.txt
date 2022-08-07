cmake_minimum_required(VERSION 3.23)
project(beebem VERSION 0.0.13)

option(BEEBEM_WITH_DEBUGGER "compile with additional logging" ON)
# TODO: Unix only
option(BEEBEM_WITH_ECONET "compile with econet" ON)
option(BEEBEM_REALTIME_SLIDER "compile with realtime slider on slide bar" OFF)
option(BEEBEM_WELCOME_MESSAGE "compile with welcome message" OFF)
option(BEEBEM_FULLSCREEN_FPS "enable full screen FPS indicator" OFF)
option(BEEBEM_SYSTEM_CP "use system cp instead of C file copy" OFF)
option(BEEBEM_FORCE_COLORMAP "force colormap for 8-bit displays" OFF)

if (BEEBEM_WITH_DEBUGGER)
  message(STATUS "enabling debugger")
  add_definitions(-DWITH_DEBUG_OUTPUT=1 -DEG_DEBUG=1)
else()
  message(STATUS "disabling debugger")
  add_definitions(-DWITHOUT_LEVEL_INDICATOR=1, -DWITHOUT_SHENANIGANS=1)
endif()

if (BEEBEM_WITH_ECONET)
  # TODO: conditional build perhaps
  message(STATUS "enabling econet")
  add_definitions(-DWITH_ECONET=1)
endif()

if (BEEBEM_REALTIME_SLIDER)
else()
  message(STATUS "disabling realtime slider")
  add_definitions(-DWITHOUT_REALTIME_SLIDER=1)
endif()

if (BEEBEM_WELCOME_MESSAGE)
else()
  message(STATUS "disabling welcome message")
  add_definitions(-DWITHOUT_WELCOME_MESSAGE=1)
endif()

if (BEEBEM_FULLSCREEN_FPS)
  message(STATUS "enabling FPS in fullscreen")
  add_definitions(-DWITH_FS_FPS=1)
endif()

if (BEEBEM_SYSTEM_CP)
  message(STATUS "enabling system `cp`")
  add_definitions(-DWITH_SYSTEM_CP=1)
endif()

if (BEEBEM_FORCE_COLORMAP)
  message(STATUS "enabling forced colormap")
  add_definitions(-DWITH_FORCED_CM=1)
endif()

add_definitions(-DWITH_UNIX_EXTRAS=1 -DREG_FILENAME=beebem.registry)

find_package(SDL2 REQUIRED)
message(STATUS "found SDL ${SDL_VERSION}")

find_package(GTK2 REQUIRED)
message(STATUS "found GTK2 ${GTK2_VERSION}")
include_directories(${GTK2_INCLUDE_DIRS})

add_subdirectory(src)
add_subdirectory(data)
add_subdirectory(doc)
