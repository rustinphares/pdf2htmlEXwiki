>###- 欲速则不达。<br>- Haste makes waste.

# Building pdf2htmlEX

Because of its intimate use of *specific* versions of both 
[Poppler](https://poppler.freedesktop.org/) and 
[FontForge](https://fontforge.org/en-US/),
cleanly building `pdf2htmlEX` is rather more complex than 
normal. 

The (shell) scripts in the [`buildScripts` directory](https://github.com/pdf2htmlEX/pdf2htmlEX/tree/master/buildScripts) help automate this mutli-stage process. 

For all but the most experienced programmers, we *strongly* encourage you 
to use these scripts to build `pdf2htmlEX`. 

### Downloading precompiled versions

For most users, you *probably really want to simply* download one of the 
[precompiled versions of 
`pdf2htmlEX`](https://github.com/pdf2htmlEX/pdf2htmlEX/releases): 

- As a [Debian archive](Download-Debian-Archive)
- As an [Alpine tar archive](Download-Alpine-Tar-Archive)
- As an [AppImage](Download-AppImage)
- As a [Docker image](Download-Docker-Image)

# Environment

pdf2htmlEX can be built in any Unix-like environment:
* **GNU/Linux:**
  `pdf2htmlEX` is currently built and released inside Ubuntu
  (Bionic, Eoan, and Focal), Alpine 3.12 docker containers,
  as well as Ubuntu-Bionic on Travis, so `pdf2htmlEX` is
  *known* to build on any Debian based distribution.

  The current `buildScripts` assume the use of either `apt` 
  (Debian) or `apk` (Alpine) for (automatic) installation of
  all required dependencies. These scripts should be easily 
  modified for other distributions.
* **macOS**:
  While it should in principle be possible to build on macOS,
  unfortunately we currently have no access to a development/testing
  environment with which to ensure the `buildScripts` are
  adequately tuned to build on macOS.

  **NOTE** that the existing [`homebrew`](https://brew.sh/)
  [build script](https://github.com/Homebrew/homebrew-core/blob/master/Formula/pdf2htmlex.rb)
  is *not* up to date and will fail.

  *Offers of help and/or temporary access to development/testing
  machines would be greatly appreciated.*

* **Windows 10 with the [Windows Subsystem
  for Linux](https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux)**:

  The Debian(Apt) versions of our build scripts should build `pdf2htmlEX` (untested).

  The AppImage or Debian archive binary release objects *are* reputed to work.

* **Android**: Have a look at [Vilius Sutkus](https://github.com/ViliusSutkus89)'s [pdf2htmlEX-Android](https://github.com/ViliusSutkus89/pdf2htmlEX-Android).

# Building yourself

To build `pdf2htmlEX` on a Debian/Apt related machine, inside the root 
directory of a fresh clone of the 
[pdf2htmlEX/pdf2htmlEX](https://github.com/pdf2htmlEX/pdf2htmlEX) 
repository, type: 

```
    ./buildScripts/buildInstallLocallyApt
```

This will automatically install all required development tools and 
libraries, and then proceed to download and statically compile the 
required versions of both Poppler and FontForge before compiling and 
installing `pdf2htmlEX` into `/usr/local/bin`. 

**NOTE:** at the moment this will **only** work on machines with a 
[Debian](https://www.debian.org/) based distribution. such as 
[Ubuntu](https://ubuntu.com/), [Linux Mint](https://linuxmint.com/), etc. 

**NOTE:** there is currently an *experimental* build script, 
`./buildScripts/buildInstallLocallyAlpine`, for builds in Alpine 
environments. 

## Dependencies

The definitive list of build dependencies can be found in the following scripts:

1. [getBuildToolsAlpine](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/getBuildToolsAlpine) for Alpine Linux
2. [getBuildToolsApt](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/getBuildToolsApt) for Debian based systems
3. [getDevLibrariesAlpine](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/getBuildToolsAlpine) for Alpine Linux
4. [getDevLibrariesApt](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/getBuildToolsApt) for Debian based systems

## Build options

To build `pdf2htmlEX` you require static versions of the Poppler and FontForge libraries in specific 'well-known' locations.

An automatic build uses `cmake` to build all of Poppler, FontForge and `pdf2htmlEX`.

The definitive list of cmake build options can be found in the following scripts:

1. [buildFontforge](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/buildFontforge)
2. [buildPdf2htmlEX](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/buildPdf2htmlEX)
3. [buildPoppler](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/buildPoppler)

# Why such a complex build system?

## The problem

To provide its full functionality, the `pdf2htmlEX` sources make direct 
use of source code and unexposed methods from both the Poppler and 
FontForge projects. Unfortunately the source code in the Poppler and 
FontForge projects that the `pdf2htmlEX` uses changes regularly.

This means that the `pdf2htmlEX` souce code *must* be updated regularly to 
match *specific releases* of both Poppler and FontForge. 

Unfortunately, the installed versions of both Poppler and FontForge in 
most Linux distributions, lag the official releases of both of these 
projects. Even worse few distributions install the same versions.

This means that it is nearly impossible for the `pdf2htmlEX` code to 
'predict' which version of Poppler or FontForge will be installed on a 
given user's machine. 

## Our solution

While we *could* keep multiple versions of the `pdf2htmlEX` source code, 
each version matched to a particular distribution's installed versions of 
Poppler and FontForge, this would be a logistic and testing 'nightmare'. 

Instead, when building `pdf2htmlEX`, we download specific versions of both 
the Poppler and FontForge sources (usually the most recent), and then 
compile *static* versions of the Poppler and FontForge libraries which are 
then *statically* linked into the `pdf2htmlEX` binary. 

This means that the `pdf2htmlEX` binary is completely independent of any 
locally installed versions of either Poppler or FontForge.

However, to get the matched versions of Poppler and FontForge and then 
compile them statically, *our* build process becomes much more complex 
than a "simple", `configure, make, make install` cycle. 

Hence there are a large number of shell scripts in the [`buildScripts`
directory](https://github.com/pdf2htmlEX/pdf2htmlEX/tree/master/buildScripts)
each of which automates one 'simple' step in the overall build process. 

## [The gory details ...](https://github.com/pdf2htmlEX/pdf2htmlEX/blob/master/buildScripts/Readme.md#the-gory-details-)
