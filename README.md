This is a copy of the 3DMMForever code that has no modifications to make it works on modern operating systems, in fact it has no modifications to the base code. It's intended for those who (for reasons that are hard to name, but it can't hurt to have it) want an exact but buildable copy of the source code for the original 1996 release.

## Building instructions

- Make sure this repo is checked out to a folder with a short name, ideally right on the root of a drive (i.e. C:\3d).
- You will need Visual C++ 2.1's dev tools (located under MSVC21\BIN on its installer disk) on your path. Modern compilers dislike some of the pre C++98 conventions.
- Set these environment variables:
  - set MSVCNT_ROOT=C:\msvc21
  - set PATH=%MSVCNT_ROOT%\bin;%PATH%;
  - set INCLUDE=%MSVCNT_ROOT%\include
  - set LIB=%MSVCNT_ROOT%\lib
- From the root of this repo, run ```setvars.bat``` you can change the values in this script to change what your build will target.
  - Environment variables used by the build:
    - SOC_ROOT: Path to root of repo (where this README.md is)
    - KAUAI_ROOT: Path to Kauai: %SOC_ROOT%\kauai
    - ARCH: Operating system to build for
      - WIN: Windows
      - MAC: Macintosh 68k
    - INCLUDE: Set to the MSVC include directories, plus:
      - %SOC_ROOT%\INC
      - %SOC_ROOT%\BREN\INC
      - %SOC_ROOT%\SRC
      - %KAUAI_ROOT%\SRC
    - UNICODE: If set to non-empty, build Unicode instead of ANSI
    - TYPE: Sets build type
      - DAY: Debug, incremental (daily?)
      - HOME: Debug, not incremental
      - SHIP: Release
      - DBSHIP: Release, with linker debug output
    - BLD_TYPE_DIR: Name of directory under OBJ to place binaries. **This will be set automatically by the Kauai makefiles.**
      - WINS for ANSI release builds
      - WINUS for Unicode release builds
      - WIND for ANSI debug builds
      - WINUD for Unicode debug builds
    - CHIP: Set to use optimized assembly language implementations of some functions in Kauai
      - IN_80386: Intel 80386
      - MC_68020: Motorola 68020 (for Macintosh)
      - If not set, just use the C implementation
- Locate and place font files (see [FONTS.md](FONTS.md))
- Build Kauai
  - `cd %SOC_ROOT%\kauai`
  - `nmake all`
- Build 3D Movie Maker
  - `cd %SOC_ROOT%`
  - `nmake all`

### Known Issues

- Compilation of `SITOBREN.EXE` is disabled
  - This requires the SoftImage SDK "DKIT" to compile

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.

This repo includes a build from 1995 of BRender from Argonaut software. Approval to open source BRender as MIT was given in an email from Jez San, former CEO of Argonaut. Other versions of BRender exist at https://github.com/foone/BRender-v1.3.2 and https://github.com/foone/BRender-1997 Thanks to Jez and the whole BRender team for their hard work on this amazing engine. A full historical list of BRender contributors is available at https://github.com/foone/BRender-v1.3.2/blob/main/README.md 

This repo does NOT include the SoftImage SDK "./DKIT" from 1992.


