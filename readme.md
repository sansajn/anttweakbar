# About

This is AntTweakBar library fork with scons build tool support.

To build library,

- install dependencies with
```bash
sudo apt install libsdl1.2-dev libglfw3-dev freeglut3-dev
```
command

- run
```bash
scons -j8
```
command.

AntTweakBar is build as both static (`libanttweakbar.a`) and shared (`libanttweakbar.so`) library.

To install

- run
```bash
sudo scons install
```
command which install `libanttweakbar.so` into `/usr/local/lib` directory.

- run
```bash
sudo ldconfig
```
to update linker database.



AntTweakBar development library
-------------------------------


AntTweakBar is a small and easy-to-use C/C++ library that allows programmers
to quickly add a light and intuitive GUI into OpenGL and DirectX based 
graphic programs to interactively tweak parameters.

This package includes the development version of the AntTweakBar library 
for Windows, GNU/Linux and OSX, and some program examples (sources + binaries).

For installation and documentation please refer to:
http://anttweakbar.sourceforge.net/doc


