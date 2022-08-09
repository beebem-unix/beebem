# beebem for UNIX

http://beebem-unix.bbcmicro.com/

Imported to github with permission from David Eggleston

see [doc/README.txt](doc/README.txt) for the original Beebem for Windows README.

## Compiling and installing

### Install in home account (for a specific user only)

an out-of-tree build is preferred:

```
$ mkdir _build && cd _build
$ cmake -DCMAKE_INSTALL_PREFIX=$HOME/beebem ..
$ make
$ make install
```

### Install as root (global install for all users)

```
$ mkdir _build && cd _build
$ cmake -DBEEBEM_ENABLE_ECONET ..
$ make
$ sudo make install
```

### Options

there are a number of options available to be passed to the cmake command line
that can enable or disable features.  they are:

* `BEEBEM_WITH_DEBUGGER`: enable additional logging
* `BEEBEM_ENABLE_ECONET`: enable econet for networking
* `BEEBEM_DISABLE_REALTIME_SLIDER`: disable the realtime slider on any slide bars
* `BEEBEM_DISABLE_WELCOME_MESSAGE`: disable the (annoying) welcome message
* `BEEBEM_ENABLE_FULLSCREEN_FPS`: enable the FPS indicator when in fullscreen
* `BEEBEM_ENABLE_SYSTEM_CP`: use the system `cp` instead of a (slower) C implementation
* `BEEBEM_ENABLE_FORCE_COLORMAP`: force a colormap for 8-bit displays
