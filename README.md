# General Build Instructions

**1)** Set `WINBUILDS_ROOT` environment variable to specify a target directory. If WINBUILDS_ROOT is not set it is assumed to be the same directory where the .vcxproj file resides. Developer packages will be created in %WINBUILDS_ROOT% according to the following schema:

`$(WINBUILDS_ROOT)build_msvc16_$(Platform)/$(Configuration)/bin/`:
<br>.exe , .dll, .exp, .pdb go here

`$(WINBUILDS_ROOT)build_msvc16_$(Platform)/$(Configuration)/lib/` :
<br>.lib go here

`$(WINBUILDS_ROOT)build_msvc16_$(Platform)/$(Configuration)/include/` :
<br>.h go here

**2)** Open `Windows\VS2019\*.sln` with Visual Studio 2019  or newer and rebuild.

## Building Libraries
For library projects, both static and shared libraries will be produced.
The static libraries will assume static C and C++ runtimes and the shared
libraries will link to dynamic C and C++ runtime libraries.

Static libraries do not link to their dependencies, shared libraries do.

Shared libraries with static runtimes and static libraries with dynamic
runtimes are normally not produced but you are welcome to add those
build options if you need them or you just feel like it.

Target naming convention:
```
<name>dll.dll - dynamic library
<name>dll.lib - import library
<name>lib.lib - static library
```

This naming schema produces names different from the original projects, but it is consistent, and it is believed that it is easier to use than ad-hoc names.