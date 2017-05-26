# OpenGL C++ Boilerplate

A cross-platform boilerplate project for modern OpenGL, utilising GLFW for context management, GLEW for handling OpenGL extensions, and GLM for mathematics.


    git clone git@github.com:andersonfreitas/opengl-boilerplate.git --recursive


## Build

    mkdir build && cd build
    cmake ..
    make

### Building with XCode

    mkdir xcode && cd xcode
    cmake -G "Xcode" ..

Then open the generated `Project.xcodeproj` project.

If you don't have CMake installed on your Mac, the easist way is to install is with [Homebrew](http://brew.sh) using `brew install cmake`

### Building with Visual Studio

CMake comes with a diverse options of [generators](http://www.cmake.org/cmake/help/v2.8.8/cmake.html#section_Generators). Use the CMake GUI on Windows to automatically create a project solution based on this project.

Set your source directory to here, and the build directory to build, i.e.:

    Path to source directory: C:\some\where\opengl-boilerplate
    Path to build directory: C:\some\where\opengl-boilerplate\build

## Dependencies

 * [GLFW](https://github.com/glfw/glfw)
 * [GLEW](http://github.com/nigels-com/glew.git)
 * [GLM](https://github.com/g-truc/glm)
 * [CMake](http://www.cmake.org/)
