add_library(eg gui.h sdl.c sdl.h
  functions.c functions.h types.h
  log.h line.h log.c
  messagebox.c messagebox.h messagebox_private.h
  window.c window.h window_private.h
  widget.c widget.h widget_private.h widget_shared.c widget_shared.h
  label.c label.h label_private.h
  button.c button.h button_private.h
  box.c box.h box_private.h
  tickbox.c tickbox.h tickbox_private.h
  togglebutton.c togglebutton.h togglebutton_private.h
  radiobutton.c radiobutton.h radiobutton_private.h 
  radiogroup.c radiogroup.h radiogroup_private.h 
  tabgroup.c tabgroup.h tabgroup_private.h 
  tabpage.c tabpage.h tabpage_private.h 
  slidebar.c slidebar.h slidebar_private.h 
  progressbar.c progressbar.h progressbar_private.h)

target_include_directories(eg PRIVATE ${CMAKE_BINARY_DIR})
target_include_directories(eg PRIVATE ${CMAKE_SOURCE_DIR}/src)
target_include_directories(eg PRIVATE ${SDL_INCLUDE_DIRS})
target_compile_options(eg PRIVATE -Wall -Werror -Wno-format-security)
