>###- 欲速则不达。<br>- Haste makes waste.

#### Environment
pdf2htmlEX can be built in a Unix-like environment:
* GNU/Linux (for Ubuntu 12.10+, Fedora)
* macOS
* Windows/Cygwin
* Windows/Mingw-w64
* Windows/MinGW, with some modifications to pdf2htmlEX. See [pdf2htmlEX on TeX Wiki](http://oku.edu.mie-u.ac.jp/~okumura/texwiki/?pdf2htmlEX) (in Japanese), special thanks to Haruhiko Okumura.

#### macOS

An easy way to install pdf2htmlEX on macOS is to use [brew](http://brew.sh/).
After installing brew, open a terminal:
``` bash
brew install pdf2htmlEX
```
#### Windows
An easy way to build pdf2htmlEX on Windows is MSYS2 + mingw-w64.
[Build-pdf2htmlEX-on-Windows](https://gist.github.com/cnstar9988/3571c66b49050d98df92142dc19fbb00) (in Chinese)


#### Dependencies
Fedora
``` bash
sudo yum install  cmake gcc gnu-getopt java-1.8.0-openjdk libpng-devel fontforge-devel cairo-devel poppler-devel libspiro-devel freetype-devel  poppler-data libjpeg-turbo-devel git make gcc-c++
```

Manual

* CMake, pkg-config
* GNU Getopt
* C++ Compiler that supports C++11, for example
    * GCC >= 4.6.3
    * A recent version of Clang
* libspiro
* **poppler** >= 0.25.0 with xpdf headers (compile with `--enable-xpdf-headers`)
    * Install **libpng** (and headers) BEFORE you compile poppler if you want PNG background images generated
    * Install **libjpeg** (and headers) BEFORE you compile poppler if you want JPG background images generated
    * Install **poppler-data** if your want CJK support
* **fontforge** (with header files)
    * A recent version or [my fork](https://github.com/pdf2htmlEX/fontforge/tree/pdf2htmlEX), use the `pdf2htmlEX` branch, which is a modified version of the 20140101 release.
    * Older versions may or may not work.

#### Optional

* To generate SVG background images and process Type 3 fonts
    * cairo >= 1.10.0 with SVG support
    * FreeType
    * Add `-DENABLE_SVG=OFF` to `cmake` to disable it.
* To add hinting information for TTF fonts
    * ttfautohint
    * Run pdf2htmlEX with `--external-hint-tool=ttfautohint`
* To optimize CSS and JavaScript code with YUI Compressor and closure-compiler
    * java >= 6

#### Compiling

    git clone git://github.com/coolwanglu/pdf2htmlEX.git
    cd pdf2htmlEX
    cmake . && make && sudo make install

Stable releases can be found at <https://github.com/pdf2htmlEX/pdf2htmlEX/releases>.

In order to create the debug version, add `-DCMAKE_BUILD_TYPE=Debug` to `cmake`.

#### Troubleshooting

If you installed poppler or fontforge into a place other than `/usr` (If you install them from source code, they are installed to `/usr/local` by default), you need to set up environment variables for pkg-config, and maybe also `INCLUDE_PATH`, `LIBRARY_PATH` and `LD_LIBRARY_PATH` because some GNU/Linux distributions do not set them up for you (e.g. Fedora). If you are not sure about this, just install those libraries to `/usr` by passing `--prefix=/usr` to `configure`.

If you see error messages about:

 - `goo/GooString.h`, read the dependencies again, `poppler` should be compiled with `--enable-xpdf-headers`
 - `spiroentrypoints.h`, install header files of libspiro
 - `undefined reference of Py_xxx`, install header files of python-2.x
 - `libintl.h`, install gettext and set your system include path accordingly.
 - `glib.h: No such file or directory`, install the development header files of `glib-2.0`, and make sure that the location of `glib.h` is in `INCLUDE_PATH`.

#### Hacker's magical scripts

These scripts have been reported to be useful in various situations. They have NOT been tested by pdf2htmlEX's authors, use at your own risk! If you want to contribute, please create your own gist somewhere, and post a link and description here.

- [rajeevkannav/pdf2htmlEX.sh](https://gist.github.com/rajeevkannav/d07f822e209a22d07176) install on Ubuntu 15.04



