## Docker and C++
### A new world for cross-compiling*
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
* Herbceptions - Value-Based Exception Proposal
* Gradle C++ Support in CLion
* JFrog SwampUP - Packaing C++ with Conan Track

---
### OSS Lib of the Month
* Emscripen
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
### Definition : Containers (Docker)
*A container image is a lightweight, stand-alone, executable package of a piece of software that includes everything needed to run it: code, runtime, system tools, system libraries, settings.*

---
### Compiling with Containers
* Our "application" is a C/C++ compiler
* Containers exist for many platforms
* Windows + linux container ~= cross-compilation

---
![Carsim Logo](/assets/image/docker-host-graphic.png)

---
![Carsim Logo](/assets/image/wcol-architecture.png)

---
### Windows Subsystem for Linux (WSL)
* Another option to be aware of
* Actual linux within windows
* Again, ~= cross-compilation
* Can run docker in WSL

---
![Carsim Logo](/assets/image/linux-subsystem-for-windows.png)

---
### Docker Basics
* On Linux - Shares Kernel, Any Distro/Arch
    * Processes all appear under `top`
    * Multiple options for segregating access
* On Windows - Much more complex
    * Windows Containers share Windows Kernel
    * Linux Containers share Linux Kernel
    * Kernels provided by Hyper-V
    * Can only run Windows OR Linux
    
---
### Docker Basics
* On Linux - Shares Kernel, Any Distro/Arch
* On Windows - Much more complex
    * Windows Containers share Windows Kernel
    * Linux Containers share Linux Kernel
    * ~Linux Kernel Provided by MobyLinux VM~
    * ~Can only run Windows OR Linux~
    * Linux containers now use "LinuxKit"
    * Still requires HyperV, but no VM
    * Linux and Windows side-by-side

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
### Common Docker Uses - Web Software
* Ease developer collaboration
* Has become a standard "runtime unit"
* Alternative to one-VM-per-app-instance
* More efficient, universal, automatable
* Runs application in more ephemeral way
* Continuous integration - automated builds

---
### Common Docker Uses - Native Software
* Cross-building native applications
    * Locally on developer machine
    * Continuous integration
    
---
### Docker Workflow
* Write (or copy) a recipe: "Dockerfile"
* `docker build` : creates an image
* `docker run` : starts a container
* `docker push` : upload to dockerhub
OR
* `docker run` existing image from dockerhub

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
* Choose an OSS library on Github
* Compile with Windows Container
* Compile with Linux Container
* Connect with Visual Studio for Debug






