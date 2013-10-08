#### Dependencies

* CMake, pkg-config
* GNU Getopt
* compilers support C++11, for example
 * GCC >= 4.4.6
 * I heard about successful build with Clang 
* **poppler** >= 0.20.0 with xpdf headers (compile with **--enable-xpdf-headers**)
 * Install **libpng** (and headers) BEFORE you compile poppler if you want PNG background images generated
 * Install **libjpeg** (and headers) BEFORE you compile poppler if you want JPG background images generated
 * Install **poppler-data** if your want CJK support
* **fontforge** (with header files)
 * git version is recommended
* [Optional] SVG Support, for generating SVG background images and converting Type 3 fonts
 * cairo >= 1.10.0 with SVG support
 * FreeType
 * Add `-DENABLE_SVG=ON` to `cmake`
* [Optional] **ttfautohint**
 * run pdf2htmlEX with **--external-hint-tool=ttfautohint** to enable it
* [For Windows]
 * Cygwin 
 * or MinGW, with some modifications to pdf2htmlEX. See [pdf2htmlEX on TeX Wiki](http://oku.edu.mie-u.ac.jp/~okumura/texwiki/?pdf2htmlEX) (in Japanese), special thanks to Haruhiko Okumura

#### Compiling

    git clone git://github.com/coolwanglu/pdf2htmlEX.git
    cd pdf2htmlEX
    cmake . && make && sudo make install

#### Troubleshooting

If you installed poppler or fontforge into a place other than `/usr` (If you install them from source code, they are installed to `/usr/local` by default), you need to set up environment variables for pkg-config, and maybe also `INCLUDE_PATH`, `LIBRARY_PATH` and `LD_LIBRARY_PATH` because some Linux distributions do not set them up for you (e.g. Fedora). If you are not sure about this, just install those libraries to `/usr` by passing `--prefix=/usr` to `configure`.

If you see error messages about:

 - `goo/GooString.h`, read the dependencies again, `poppler` should be compiled with `--enable-xpdf-headers`
 - `spiroentrypoints.h`, install header files of libspiro
 - `undefined reference of Py_xxx`, install header files of python-2.x
 - `libintl.h`, install gettext and set your system include path accordingly.
 - `.../libfontforge.so: undefined reference to ...`, it should be caused by [a bug of FontForge](https://github.com/fontforge/fontforge/issues/465), please leave comments there such that FontForge developers may fix it soon.
  - You may try [the `tmp` branch of my fork](https://github.com/coolwanglu/fontforge/tree/tmp)
  - Try to configure FontForge with `--without-libzmq --without-x --without-iconv --disable-python-scripting --disable-python-extension`, then rebuild it. 
