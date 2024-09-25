# CPM demo

This is a CMake/CPM demo including lodepng and other libraries.

Note that it is portable: it works under both Linux and Windows.

Usage:

```
cmake -B build
cmake --build build
```

Under Linux, some dependencies are assumed. Under Ubuntu, you can satisfy them like so:

```
apt-get install ninja-build libwayland-dev libxrandr-dev libxkbcommon-x11-dev libxinerama-dev libxcursor-dev libxi-dev  libglu1-mesa-dev freeglut3-dev mesa-common-dev
```