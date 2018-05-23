## Docker and C++
#### A new world for cross-compiling
*Sponsored By Mechanical Simulation*  
![Carsim Logo](/assets/image/logo/carsim.png)
---
### Local Announcements
* Thanks to Mechanical Simulation!

---
### C++ Announcements
* CPP Now - Aspen
    * Jetbrains Trip report: 
    * https://blog.jetbrains.com/clion
* VCPKG Supports Linux and Mac
* Visual Studio Live Share Extension
* Herbceptions - Value-Based Exception Proposal
* Gradle C++ Support in CLion
* JFrog SwampUP - Packaing C++ with Conan Track

---
### OSS Lib of the Month
* Emscripten
    * https://github.com/kripken/emscripten
    * Emscripten: An LLVM-to-JavaScript Compiler
    * Tanker.io is replacing JS codebase with C++
    
---
### Questions
* Any Local Projects or Announcements?
* New ideas for topics?
    * Exploring C++ 17 Features
    * C++ Modules Proposal
	* Functional Programming in C++

---
## Docker and C++
### A new world for cross-compiling*

---
## Disclaimer
* Not actually "cross-compiling"
* Docker blurs the lines a bit
* Something functionally similar... better?
* Can replace some need for cross-compilation

---
### Definition : Cross-Compiling
*A cross compiler is a compiler capable of creating executable code for a platform other than the one on which the compiler is running. For example, a compiler that runs on a Windows 7 PC but generates code that runs on Android smartphone is a cross compiler.*

---
### Definition : Container Image
*A container image is a lightweight, stand-alone, executable package of a **piece of software** that includes everything needed to run it: code, runtime, system tools, system libraries, settings.*

---
### Compiling with Containers
* Our executable "piece of software" is:
    * build system, compiler, related env vars
* Many such C/C++ containers exist on Dockerhub
* Windows + linux container ~= cross-compilation

---
### Docker Overview
![Docker Host](/assets/image/docker-host-graphic.png)

---
### Windows Container on Windows (WCOW)
![WCOW](/assets/image/wcow-architecture.png)

---
### Linux Container on Windows   (LCOW)
![LCOW](/assets/image/lcow-architecture.png)

---
### Windows Container on Linux
* Not Supported

---
### Docker Basics
* On Linux - Shares Kernel, Any Distro/Arch
* On Windows - Much more complex
    * Windows Containers share Windows Kernel
    * Linux Containers share Linux Kernel
    * Previously: Linux Kernel Provided by VM
    * Previously: Could run Windows OR Linux
    * Linux containers now use "LinuxKit"
    * Still requires HyperV, but no VM
    * Linux and Windows side-by-side

---
### Containers on macOS
* Started using a VM for Linux Kernel
* Now uses macOS Hypervisor framework
* Similar to Windows

---
### Windows Subsystem for Linux (WSL)
* Another option to be aware of
* Actual linux within windows
* Again, ~= cross-compilation
* Can run docker in WSL

---
### Linux Subsystem for Windows
![WSL](/assets/image/wsl-architecture.png)
    
---
### Docker History
* Written in Go
* Originally only supported Linux containers
* Started to ease developer to collaboration
    * Reproducable "environment" without VM's
    * Composeable : powerful layering system
    * Minimizing "It works on my machine"
    * Mitigate depdendency hell

---
### Common Uses - Web Software
* Ease developer collaboration
* Has become a standard "runtime unit"
* Alternative to one-VM-per-app-instance
* More efficient, universal, automatable
* Runs application in more ephemeral way
* Continuous integration - automated builds

---
### Common Uses - Native Software
* Cross-building native applications
    * Locally on developer machine
    * Continuous integration
    
---
### Docker Workflow
* Write (or copy) a recipe: "Dockerfile" 
* Create, use, upload and share
```
docker build ...
docker run ...
docker push ...
```
* OR use an existing image from dockerhub
```
docker run ...
``` 

---
### Dockerfile Example
```Docker
FROM gcc:4.9
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
RUN gcc -o myapp main.c
CMD ["./myapp"]
```

---
### Dockerhub for C++
* https://hub.docker.com/_/gcc/
* https://hub.docker.com/r/rsmmr/clang/
* https://hub.docker.com/r/burningdaylight/docker-mingw-qt5/

---
### Dockcross from Kitware
* Collection of images with GCC and CMake
* Each supports different "niche" platform 
* Largely based on QEMU emulators
* https://hub.docker.com/r/dockcross/
* https://github.com/dockcross/dockcross

---
### Demo Time
* Build a windows container with MSVC
* Build a linux container with GCC
* Take some C++ code
* Compile with our Windows Container
* Compile with our Linux Container
* Compile with a Dockcross Container (if time)


---
### Demo Time
* Build a windows container with MSVC
* Build a linux container with GCC
* Take some C++ code
* Compile with our Windows Container
* Compile with our Linux Container
* Compile with a Dockcross Container (if time)

---
### Dockcross containers used
* dockcross/windows-x64
* dockcross/android-arm
* dockcross/browser-asmjs

---
### Build Images from Dockerfile
While in directory with Dockerfile  
* See directory: win17134.1-vctools
```
docker build -t msvc-builder .
```
* See directory: ubuntuartful-gcc72
```
docker build -t ubuntu-builder .
```
---
### Get Interactive Shell to Container

*Note - Lines are manually wrapped*
* Linux
```
docker run --rm -it -v %CD%:/work 
<image_name> /bin/bash
```
* Windows
```
docker run --rm -it
-v %CD%:C:\users\ContainerAdministrator 
<image_name> cmd
```
*Note - **cmd** can be replaced with **powershell***
---
### Build App In Container
Here, we use the container like a standalone executable, (the way it was intended!).  
```
set IMAGE_NAME=android-arm64
set CMD=docker run --rm
set CMD=%CMD% --platform=linux
set CMD=%CMD% -v %CD%:/work
set CMD=%CMD% dockcross/%IMAGE_NAME%
set CMD=%CMD% /bin/sh -c
set CMD=%CMD% "mkdir build-%IMAGE_NAME% &&
set CMD=%CMD% cd build-%IMAGE_NAME% &&
set CMD=%CMD% cmake .. &&
set CMD=%CMD% cmake --build ."
%CMD%
```
