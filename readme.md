![Build](https://github.com/AcademySoftwareFoundation/openfx/actions/workflows/build.yml/badge.svg)

# OpenFX image processing plug-in standard

The authoritative source for information about OFX is http://openeffects.org/

* [OpenFX Build Instructions](https://github.com/AcademySoftwareFoundation/openfx/blob/master/install.md)
* [OpenFX Documentation](https://openfx.readthedocs.io/en/latest) - start here
* [OpenFX Documentation: Reference](https://openfx.readthedocs.io/en/latest/Reference)
* [Programming Guide By Example](https://openfx.readthedocs.io/en/latest/Guide)
* [OpenFX Wiki](https://wiki.aswf.io/pages/viewpage.action?pageId=49844871) 

Here are some [Ways to get involved](https://tac.aswf.io/engagement/#OpenFX) with OpenFX.

## Why a Standard?
VFX plug-in vendors were frustrated for years because host application vendors created proprietary plug-in interfaces. As a result, each plug-in vendor had to port their plug-ins to all the different hosts and hosts couldn't use each other's plug-ins, limiting the selection of effects available to artists. The need for a standard interface was clear, so Bruno Nicoletti of The Foundry led the effort to develop a standard. That standard is OFX.

OFX is a win for artists because there is no waiting for plug-in vendors to port their cool effects to your application. Once a host compositing or editing application adopts OFX, all OFX plug-ins on the market instantly become available on that host.

And OFX is a win for plug-in vendors because they can concentrate on what they do best: making cool effects

## OFX Terminology
### Host
A video compositing or editing application, such as The Foundry Nuke, Assimilate Scratch, Sony Vegas, or FilmLight Baselight
### Plug-in
Video software, such as GenArts Sapphire or RE:Vison Effects which adds a wider variety of effects to a host application.
### Open Effects
A standardized software interface between VFX host applications and plug-ins (also known as OpenFX and OFX).
### Editor
An application which allows you to manipulate a video timeline by adding, removing, and changing the in and out points of video clips. Effects, Generators, Transition, Compositors and Retiming effects are commonly used in editors.
### Compositor
An application which allows you build a video clip by layering video clips, still images, and effects.

## Contributing

Please read the [Contribution Guidelines](https://github.com/ofxa/openfx/wiki/Extending-OpenFX-Guidelines) for how to submit pull requests for fixes and changes to the standard.

# Building

You can build the examples, support lib, and host support lib using Conan and CMake

## Prerequisites

Install cmake (version 3.28 or greater recommended):
- Mac: `brew install cmake`
- Windows: `choco install cmake`
- Linux: `apt install cmake`

Install conan (version >= 2.1.0 recommended) using pip (and python3)
- `pip3 install 'conan>=2.1.0'`


## Build

On all OSes, you should be able to use `scripts/build-cmake.sh` which does something like this:

```sh
# Install dependencies from conanfile.py
% conan install -s build_type=Release --build=missing .
# Configure cmake to build into Build folder, and build example plugins
# Note: The preset name is platform and conan version dependent. The preset name for your specific platform will be printed by the "conan install" command.
% cmake --preset default -DBUILD_EXAMPLE_PLUGINS=TRUE
# Do the build
# Note: The build directory is also generator specific. If the preset name is something like "release", then you'll likely need to use "--build build/Release" instead of "--build build"
% cmake --build build --config Release
```

This should build with the default Visual Studio on Windows and
Makefiles with gcc on Linux and Mac. You can use alternative build
systems supported by CMake like `ninja` if you want (not covered
here).


# Building Docs

See instructions in Documentation/README.md.
