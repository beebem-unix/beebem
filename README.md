# beebem for UNIX

http://beebem-unix.bbcmicro.com/

Imported to github with permission from David Eggleston

## Installation

### Install in home account (for a specific user only):
Extract the source code tarball:

```
./configure --prefix=$HOME/test --enable-econet
make
make install
```

### Install as root (global install for all users):
```
tar zxvf beebem-0.0.8.tar.gz
cd beebem-0.0.8

./configure --enable-econet
make
make install-strip
```
