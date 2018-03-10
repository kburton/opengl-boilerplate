# OpenGL C Boilerplate

A cross-platform boilerplate project for modern OpenGL, utilising GLFW for
context management, GLEW for handling OpenGL extensions, and
[linmath.h](https://github.com/datenwolf/linmath.h) for mathematics.


    git clone https://github.com/kburton/opengl-boilerplate-c.git --recursive


## Build

CMake can generate a vast number of different project types supporting a diverse
range of IDEs and build utilities: however, CMake can't build projects on its
own.

Depending on your system and set up, the typical generators are:
* `Unix Makefiles`

macOS:
* `Xcode`

Windows:
 * `Visual Studio 15 2017`
 * `Visual Studio 15 2017 Win64`

You can generate each project from the command line by changing directory (`cd`)
to the empty `build` directory, and running:

    cmake .. -G '<your generator goes here>'
    <open the generated project>

### Using the `cmake-gui`

Set your source directory to here, and the build directory to `build`, i.e.:

    Path to source directory: /some/where/opengl-boilerplate-c
    Path to build directory: /some/where/opengl-boilerplate-c\build

Then, select 'Configure', picking a supported generator from the pop-up that
appears, and finally 'Generate'.

You can now open this generated project with 'Open Project'.

## Dependencies

Some of these dependencies, marked as _included_, are distributed either in source, or as a git submodule.
Make sure you've cloned with `--recursive`, or use `git submodule init; git submodule update` to fetch them.

 * [Graphics Library Framework (GLFW)](https://github.com/glfw/glfw): included, handles setting up the GL context
 * [OpenGL Extension Wrangler (GLEW)](http://github.com/nigels-com/glew.git): included, manages GL extensions
 * [linmath.h](https://github.com/datenwolf/linmath.h): included only for convenience later on during app development
 * [CMake](http://www.cmake.org/): **required**, used to generate
