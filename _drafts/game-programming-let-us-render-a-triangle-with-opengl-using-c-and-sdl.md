---
layout: post
title: 'Game Programming: Let Us Render a Triangle With OpenGL Using C++ and SDL'
subtitle: Part 3 - The Game Code
date: 2021-04-10 14:28:42
background: /images/createGames/game_dev.jpg
---
So, we have setup our environment for development and we've automated the build process to make our live easier. Now we have to write the actual game code to render our triangle

We start by including the SDL and glew headers to create our window and call openGL functions
```
//Using SDL, SDL OpenGL, GLEW, standard IO, and strings
#define SDL_MAIN_HANDLED
#include <SDL2\SDL.h>
#include <gl\glew.h>
#include <SDL2\SDL_opengl.h>
#include <gl\glu.h>

#include <iostream>
```



Declare the following variables:

```
//Screen dimension constants
const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
//The window we'll be rendering to
SDL_Window* gWindow = NULL;

//OpenGL context
SDL_GLContext gContext;

const char *vertexShaderSource = "#version 330 core\n"
"layout (location = 0) in vec3 aPos;\n" // the position variable has attribute position 0
"out vec4 vertexColor;\n" // specify a color output to the fragment shader
"void main()\n"
"{\n"
"   gl_Position = vec4(aPos, 1.0);\n"
"vertexColor = vec4(0.5, 0.0, 0.0, 1.0);\n" // set the output variable to a dark-red color
"}\0";

const char *fragmentShaderSource = "#version 330 core\n"
"out vec4 FragColor;\n"
"in vec4 vertexColor;\n" // the input variable from the vertex shader (same name and same type) 
"void main()\n"
"{\n"
"   FragColor = vertexColor;\n"
"}\n\0";

unsigned int vertexShader;
unsigned int fragmentShader;

unsigned int shaderProgram;
```

Modern OpenGL requires that we at least set up a vertex and fragment shader if we want to do some rendering so we will briefly introduce shaders and configure two very simple shaders for drawing our first triangle. You can read more about shaders if you really want to understand the inner workings(you should), I will write about it in the future.

The first thing we need to do is write the shaders in the shader language GLSL (OpenGL Shading Language). We take the source codes for the shaders and store them in const C strings(fragmentShaderSource and vertexShaderSource) at the top of the code file.


Be sure to define your main like this:
```
int main(int argc, char* args[])
{}
```

Next we initialize  SDL and OpenGL context:
```
    // Initialize SDL
    SDL_Init( SDL_INIT_VIDEO );

    //Use OpenGL 3.3 core
    SDL_GL_SetAttribute( SDL_GL_CONTEXT_MAJOR_VERSION, 3 );
    SDL_GL_SetAttribute( SDL_GL_CONTEXT_MINOR_VERSION, 3 );
    SDL_GL_SetAttribute( SDL_GL_CONTEXT_PROFILE_MASK, SDL_GL_CONTEXT_PROFILE_CORE );
    
    //Create window
    gWindow = SDL_CreateWindow( "NANDGIZMOS", SDL_WINDOWPOS_UNDEFINED, SDL_WINDOWPOS_UNDEFINED, SCREEN_WIDTH, SCREEN_HEIGHT, SDL_WINDOW_OPENGL | SDL_WINDOW_SHOWN );


    //Create context
    gContext = SDL_GL_CreateContext( gWindow );

    //Initialize GLEW
    glewExperimental = GL_TRUE; 
    GLenum glewError = glewInit();
    
    //Use Vsync
    SDL_GL_SetSwapInterval( 1 );
```

The above code basically initialises SDL and OpenGL.

Next, we compile our shaders so we can use them in the application

```
vertexShader = glCreateShader(GL_VERTEX_SHADER);
    glShaderSource(vertexShader, 1, &vertexShaderSource, NULL);
    glCompileShader(vertexShader);

    // check for shader compile errors
    int success;
    char infoLog[512];
    glGetShaderiv(vertexShader, GL_COMPILE_STATUS, &success);
    if (!success)
    {
        glGetShaderInfoLog(vertexShader, 512, NULL, infoLog);
        std::cout << "ERROR::SHADER::VERTEX::COMPILATION_FAILED\n" << infoLog << std::endl;
    }


    unsigned int fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
    glShaderSource(fragmentShader, 1, &fragmentShaderSource, NULL);
    glCompileShader(fragmentShader);
    // check for shader compile errors
    glGetShaderiv(fragmentShader, GL_COMPILE_STATUS, &success);
    if (!success)
    {
        glGetShaderInfoLog(fragmentShader, 512, NULL, infoLog);
        std::cout << "ERROR::SHADER::FRAGMENT::COMPILATION_FAILED\n" << infoLog << std::endl;
    }


    // link shaders
    shaderProgram = glCreateProgram();
    glAttachShader(shaderProgram, vertexShader);
    glAttachShader(shaderProgram, fragmentShader);
    glLinkProgram(shaderProgram);
    // check for linking errors
    glGetProgramiv(shaderProgram, GL_LINK_STATUS, &success);
    if (!success) {
        glGetProgramInfoLog(shaderProgram, 512, NULL, infoLog);
        std::cout << "ERROR::SHADER::PROGRAM::LINKING_FAILED\n" << infoLog << std::endl;
    }
```

