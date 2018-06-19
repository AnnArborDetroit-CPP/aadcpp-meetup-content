## Parsing Binary Structures - Intro to Kaitai Struct
*Sponsored By Mechanical Simulation*  
![Carsim Logo](/assets/image/logo/carsim.png)
---
### Local Announcements
* Thanks to Mechanical Simulation!
* Starting in April - New Day of Month

---
### C++ Announcements
* Jacksonville Standards Committee Meeting
    * Tooling Study Group (SG15) Progress
    * Unicode Study Group (SG16) Formed
    * Optimistic to make it: Ranges "core",
        Concepts, Executors, 
        Coroutines, Modules, Contracts
        Networking, Concurrency
    * Unlikely to make it: 
      - Reflection, async, a new "future"



---
### OSS Lib of the Month
* HPX 1.1.0 - Recently Updated/Released
    - http://stellar-group.org/2018/03/hpx-1-1-0-released/
    - ParalleX: An Advanced Parallel Execution Model for 
        ScalingImpaired Applications
    
---
### Questions
* Any Local Projects or Announcements?
* New ideas for topics
	* Docker for C++
	* Boost OpenSource Libraries
    * Poco OpenSource Libraries

---
### Welcome Chris Cadwallader
* Kaitai Struct
* https://github.com/ApatheticsAnonymous/Kaitai-introduction

---
### vcpkg library 
* Install, compile and manage third party software
* Written in C++
* Works on Windows, Linux and MacOS
* Open source, available on github

---
### Install
* git clone https://github.com/Microsoft/vcpkg
* cd vcpkg
* run either .\bootstrap-vcpkg.bat or .\bootstrap-vcpkg.sh
* It will download cmake, ninja, find the compiler and compile the vcpkg executable

---
### Add packages
* Search
    - ./vcpkg search boost-any
    - ./vcpkg install boost-any
* The boost libraries can be installed individually
* The ports subdirectory contains all the available libraries
* Where is there a description of each library?

---
### Integration with Visual Studio
* .\vcpkg integrate install
* Requires admin the first time it is run
* Creates two files in:
    C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140\ImportBefore\Default\vcpkg.system.props
    C:\Users\tcw32_000\AppData\Local\vcpkg\vcpkg.user.targets
* vcpkg.system.props points to vcpkg.user.targets which points to 
   vcpkg\scripts\buildsystems\msbuild\vcpkg.targets
* sets up the properties so visual studio knows where the includes/libs are
* Adds a post build step that copies the dlls to the project so the exe will run

---
### Integration with other tools
* cmake - many projects provide CMake targets:
    -     find_package(Eigen3 CONFIG REQUIRED)
          target_link_libraries(main PRIVATE Eigen3::Eigen)
* xcode
* make
* vscode


---
### Team Configuration
* .\vcpkg integrate install should not be used by teams
* Does not scale
* Does not allow for shared packages
* Does not work well with CI
* vcpkg has an export command
* Can export any subset of the available libraries
* export to 7zip, zip, nuget, raw (uncompressed folder)

---
### Team Configuration Options
* shared directory to export to
* Use nuget on windows, this will bring the libraries to the local machine
* Location of the shared vcpkg directory can be in an environment variable

---
### Multiple enlistments
* vcpkg can be cloned to multiple locations
* A location might have libraries to explore but not publish
* A location could have a earlier library version
    - the whole repo must be checked out at the revision containing the version
    - how does this work for managing multiple old libraries?

---
### Other Commands
* vcpkg list
* vcpkg update
* git pull  - to update the local portfiles and vcpkg
* If the current installed libraries need updating, vcpkg gives you instructions.
* vcpkg integrate remove

---
### Structure of vcpkg folder where installed libraries are
* installed\x64-osx\include
* installed\x64-osx\lib
* installed\x64-osx\debug\lib

---
### Structure of ports and source
* downloads - actual zip files from the internet
* buildtrees - where the libraries are built
* packages - temporary location of includes and libs

---
### Create a library
* can be local library in a zip file
* specify zip file location
* create a directory under ports containing the CONTROL and portfile.cmake
* ./vcpkg create tims_hello_world file:///Users/tcw321/ClionProjects/tims_hello_world.zip "tims_hello_world.zip"
* ./vcpkg build tims-hello-world

---
### Create a library
* can create it from zip file on the internet
* can create it from github
* use cmake, msbuild etc as the build system
* automake??
* Use the existing port files as examples

---
### Create a library
* easy to add company projects to vcpkg

---
### Triplets
* Describe self-consistent builds of library sets
* Builds specifying same target cpu, OS, compiler toolchain and CRT linkage and preferred library type
* See current available triplets
    - vcpkg --help triplets
    - triplets subfolder


    


