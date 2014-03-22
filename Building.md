#### Environment
pdf2htmlEX can be built in a Unix-like environment:
* Linux
* OS X
* Windows/Cygwin
* Windows/MinGW, with some modifications to pdf2htmlEX. See [pdf2htmlEX on TeX Wiki](http://oku.edu.mie-u.ac.jp/~okumura/texwiki/?pdf2htmlEX) (in Japanese), special thanks to Haruhiko Okumura.

#### Dependencies
* CMake, pkg-config
* GNU Getopt
* Compilers support C++11, for example
 * GCC >= 4.4.6
 * A recent version of Clang
* **poppler** >= 0.20.0 with xpdf headers (compile with `--enable-xpdf-headers`)
 * Install **libpng** (and headers) BEFORE you compile poppler if you want PNG background images generated
 * Install **libjpeg** (and headers) BEFORE you compile poppler if you want JPG background images generated
 * Install **poppler-data** if your want CJK support
* **fontforge** (with header files)
 * A recent version should work. In case that it doesn't, try [my fork](https://github.com/coolwanglu/fontforge/tree/pdf2htmlEX)

#### Optional

* To generate SVG background images and process Type 3 fonts
 * cairo >= 1.10.0 with SVG support
 * FreeType
 * Add `-DENABLE_SVG=ON` to `cmake`
* To add hinting information for TTF fonts
 * ttfautohint
 * Run pdf2htmlEX with `--external-hint-tool=ttfautohint`
* To optimize CSS and JavaScript code with YUI Compressor and closure-compiler
 * java >= 6

#### Compiling

    git clone git://github.com/coolwanglu/pdf2htmlEX.git
    cd pdf2htmlEX
    cmake . && make && sudo make install

Stable releases can be found at <https://github.com/coolwanglu/pdf2htmlEX/releases>.

#### Troubleshooting

If you installed poppler or fontforge into a place other than `/usr` (If you install them from source code, they are installed to `/usr/local` by default), you need to set up environment variables for pkg-config, and maybe also `INCLUDE_PATH`, `LIBRARY_PATH` and `LD_LIBRARY_PATH` because some Linux distributions do not set them up for you (e.g. Fedora). If you are not sure about this, just install those libraries to `/usr` by passing `--prefix=/usr` to `configure`.

If you see error messages about:

 - `goo/GooString.h`, read the dependencies again, `poppler` should be compiled with `--enable-xpdf-headers`
 - `spiroentrypoints.h`, install header files of libspiro
 - `undefined reference of Py_xxx`, install header files of python-2.x
 - `libintl.h`, install gettext and set your system include path accordingly.
 - `.../libfontforge.so: undefined reference to ...`, it should be caused by [a bug of FontForge](https://github.com/fontforge/fontforge/issues/465), please leave comments there such that FontForge developers may fix it soon.
  - You may try [my fork](https://github.com/coolwanglu/fontforge/tree/pdf2htmlEX)
  - Try to configure FontForge with `--without-libzmq --without-x --without-iconv --disable-python-scripting --disable-python-extension`, then rebuild it. 
