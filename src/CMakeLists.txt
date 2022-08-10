add_subdirectory(gui)


add_executable(beebem main.cpp beebem_sdl.cpp windows.cpp beebem_pages.cpp
  beebem_pages_disks.cpp beebem_pages_disks.h beebem_pages.h fake_registry.c
  fake_registry.h user_config.c user_config.h serialdevices.cpp serialdevices.h
  csw.cpp csw.h 6502core.cpp atodconv.cpp avi.cpp beebmem.cpp beebsound.cpp
  beebwin.cpp cregistry.cpp debug.cpp disc1770.cpp disc8271.cpp econet.cpp
  sasi.cpp scsi.cpp serial.cpp speech.cpp sysvia.cpp tube.cpp uef.cpp
  uefstate.cpp userkybd.cpp uservia.cpp via.cpp video.cpp z80.cpp
  z80_support.cpp z80dis.cpp i386dasm.cpp i86.cpp teletext.cpp
  main.h types.h beebem_sdl.h hardware.h hardware.cpp windows.h 6502core.h
  atodconv.h avi.h beebem.h beebemrc.h beebmem.h beebsound.h beebwin.h
  cregistry.h debug.h disc1770.h disc8271.h econet.h port.h sasi.h scsi.h
  serial.h speech.h sysvia.h tube.h uef.h uefstate.h userkybd.h uservia.h
  via.h viastate.h video.h z80.h z80mem.h zlib/zlib.h zlib/zconf.h ea.h i86.h
  instr86.h osd_cpu.h teletext.h)

target_include_directories(beebem PRIVATE ${CMAKE_BINARY_DIR})
target_include_directories(beebem PRIVATE ${CMAKE_SOURCE_DIR}/src)
target_include_directories(beebem PRIVATE ${SDL_INCLUDE_DIRS})
target_include_directories(beebem PRIVATE ${GTK2_INCLUDE_DIRS})
target_link_libraries(beebem eg ${SDL_LIBRARIES} ${GTK2_LIBRARIES})
if (ZLIB_FOUND)
  target_include_directories(beebem PRIVATE ${ZLIB_INCLUDE_DIRS})
  target_link_libraries(beebem ${ZLIB_LIBRARIES})
endif()
target_compile_options(beebem PRIVATE -Wno-deprecated-declarations -Wall -Werror -Wno-format-security)

install(TARGETS beebem)
