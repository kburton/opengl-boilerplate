# OpenGL C++ Boilerplate

A cross-platform boilerplate project for modern OpenGL, utilising GLFW for context management, GLEW for handling OpenGL extensions, and GLM for mathematics.


    git clone https://github.com/galexite/opengl-boilerplate.git --recursive


## Build

CMake can generate a vast number of different project supporting a diverse range of IDEs and build utilities: CMake can't build projects on its own.

Depending on your system and set up, the typical generators are:
* `Unix Makefiles`

macOS:
* `Xcode`

Windows:
 * `Visual Studio 15 2017`
 * `Visual Studio 15 2017 Win64`

You can generate each project from the command line by changing directory (`cd`) to the empty `build` directory, and running:

    cmake .. -G '<your generator goes here>'
    <open the generated project>

### Using the `cmake-gui`

Set your source directory to here, and the build directory to `build`, i.e.:

    Path to source directory: /some/where/opengl-boilerplate
    Path to build directory: /some/where/opengl-boilerplate\build

Then, select 'Configure', picking a supported generator from the pop-up that appears, and finally 'Generate'.

You can now open this generated project with 'Open Project'.

## Dependencies

 * [GLFW](https://github.com/glfw/glfw)
 * [GLEW](http://github.com/nigels-com/glew.git)
 * [GLM](https://github.com/g-truc/glm)
 * [CMake](http://www.cmake.org/)
