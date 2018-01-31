## CMake Meta-Build System Intro and Highlights
*Sponsored By Mechanical Simulation*  
![Carsim Logo](/assets/image/logo/carsim.jpg)
---
### Announcements
* Thanks to Mechanical Simulation! 
* Visual Studio IntelliSense Enhancements for C++ Open Folder and CMake
* CLion now supports Windows Subsystem for Linux

---
### OSS Lib of the Month
* Cap'nProto
    * data interchange format
	* capability-based RPC system
	* Think JSON, except binary
	* 20x Speed increase over CJSON
	* Wire-Format + In-Memory Representation
	* Used extensively Cloudflare.com 

---
### Questions
* Any Local Projects or Announcements?
* New ideas for topics
	* Docker for C++
	* Boost OpenSource Libraries
---
### Introduction: CMake
* It's about sharing code
---
### What is a Meta-Build System?
* Lets you define an API for building your "Project"  
* Is not a build system itself
* Solves the problem of diversity in tooling
* Many Dev, Many OS, Many Compilers, Many IDE
* Allow Contributors or Users to Choose
* Describe a C or C++ project in a generic language
---
### Don't Headers describe my project?
* Headers describe the API of your C or C++ code
* Build and Compilation are a separate problem domain from code
* Infinitely more complicated for native languages
* Compilers, Standard Libraries, OS, Arch, Compiler Flags
* Shared vs Static Libraries, Code Generation, Unit Tests, Static Analysis
* 3rd Party Libraries
---
### How it works
* Detects your OS, Build systems and Compilers
* Tries to guess at what combination to use (overridable)
* Reads your file, Generates other Files

`CMakeLists.txt` --->  `cmake .` ---> `some.vcxproj`

* Optionally, will call your build system for you
---
### What it looks like
CMakeLists.txt 
```
cmake_minimum_required(VERSION 3.0)

# Set the project name
project (hello_cmake)

# Add an executable
add_executable(hello_cmake main.cpp)
```
---
### What it looks like when run
```
-- The C compiler identification is GNU 5.4.0
-- The CXX compiler identification is GNU 5.4.0
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info - done
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jerrywiltse/git-c/cmake-examples/01-basic/A-hello-cmake/build
```
---
### When to Use It
* Any OSS Project
* Any Cross-Compilation Project
* Breaking apart complex enterprise projects
* Anywhere you share code, even with yourself
---
### Extra Features
* Extremely powerful platform
* Turing-complete language
* Can Script/Automate Practically Anything
* Wide integration with tools and IDE's
---
### Problems to prepare for
* Lots of bad/old examples in blog posts and OSS projects
* Venerable Syntax, Widely Critizied, Very Ambiguous
* Easy to Go Overboard and Become Golden Hammer 
* Easy to accidentally build a monolithic super-project
* Its not perfect
---
### Key Resources
* Learn the basics
	* https://github.com/ttroy50/cmake-examples
* Must-watch, just after you learn the basics
	* https://www.youtube.com/watch?v=bsXLMQ6WgIk
	* https://www.youtube.com/watch?v=eC9-iRN2b04
* Outstanding for learning how to think about your project
---
### Lets Get Started !
* Prerequisites
	* Visual Studio 2017 15.3
	* Github
---
### Agenda
* Walk through simple C++ project 
	* Windows
	* Linux using Windows Subsystem for Linux (WSL)
* Demonstrate CTest
* Demonstrate Visual Studio Integration

