# Development Tools

- Explanation of all tools used for development

## Index

- [All Tools & Platforms](#all-tools--platforms)
- [GitHub Organizations](#github-organizations)
- [Tools for Software Development](#tools-for-software-development)
- [External Tools](#external-tools)

## All Tools & Platforms

- Dependency/deployment diagram of all tools and platforms:
![development-tools](_images/development-tools.drawio.png)

1. Fetch project files to begin development
2. Make source code changes, and upon careful review and building/testing for both MCU/Windows development platform, push source code changes
3. Pull up-to-date source code from GitHub and build source code to generate binaries
4. Deploy firmware to micromouse over JTAG
- These tools should be solutions to:
  - Manage development and integration of all software parts
  - Allow anyone to work on anything independently w/ no waiting for others or hardware
  - Avoid asking critical questions at the end when all development parts are coming together
  - Eliminating crunch time debug sessions
- We can change anything if we find that we're using the wrong approach

## GitHub Organizations

- A central location for everything related to our micromouse development

- **Mouse Unit 07 Kanban**
  - Allows for smaller chunks of development to keep things moving in parallel
  - All tasks laid out and allocated as we each complete tasks
- **discussions repo**
  - Saves all useful communication we do (meeting, chatting) to look back at
  - We can safely forget things and know where to look back
- **[development reference] repos**
  - Unifies all intel, documentation, guides, etc to a single place for everyone to refer to
- **[archive] repos**
  - Outdated repos for reference
- **[hardware] repos**
  - Hardware schematics, layouts, design explanation documents, etc for reference and version control
- **[software] repos**
  - Software project repos

## Tools for Software Development

- **CMake**
  - Unified build configuration generator- configures and builds projects in place of an IDE
  - Allows for:
    - Easy swapping of implementation files- decouples build target control from source code
    - Automated builds over command line
    - Running unit tests w/ builds
- **CppUTest**
  - C/C++ unit testing harness
- **gcov**
  - Provides unit testing coverage
- **CppCheck**
  - Checks for memory leaks, unsafe code, etc
- **Clang-format**
  - Checks for formatting like tabs, spaces, etc
- **Docker**
  - ...Shelved until we migrate to a new MCU that has an associated Linux toolchain
  - Unifies all development tools and environment related changes to a single place
  - Docker container will be the superset of all needed tools and environment settings (to be separated as needed as container gets too bloated of tools and responsibilities)
  - Great for both development, and automated regression testing
- **Conan**
  - ...Shelved until we migrate to a new MCU that has an associated Linux toolchain
  - We want to split software up into packages to:
    - Allow anyone to develop any layer independently via TDD/mocks/fakes
    - Apply modularity to have software that's ready to adapt to change
  - Conan is a modern package manager that works w/ Jenkins, CMake, JFrog Artifactory

## External Tools

- **YouTube**
  - Storage for all videos for reference
- **Discord**
  - Untracked communication
- **Fusion 360**
  - 3D model development
  - Schematic/PCB development
- **Jenkins**
  - Checks new source code pushed to GitHub w/ existing package artifacts to let an engineer know whether their new code works w/ all the other existing packages
  - Can run a Docker container identical to development Docker container to run the exact same procedure, but with all existing software packages
  - ...Shelved until we migrate to a new MCU that has an associated Linux toolchain
- **JFrog Artifactory**
  - Stores and centralizes build artifacts (package binaries) and Docker images
  - Also serves as version control
  - Popular build artifact repo choice that supports Conan
  - Nexus is also popular, but requires paid tier for Conan support
  - ...Shelved until we migrate to a new MCU that has an associated Linux toolchain
