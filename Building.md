### Building

#### Dependencies

* CMake, pkg-config
* GNU Getopt
* compilers support C++11, for example
 * GCC >= 4.4.6
 * I heard about successful build with Clang 
* **poppler** >= 0.20.0 with xpdf headers (compile with **--enable-xpdf-headers**)
 * Install **libpng** (and headers) BEFORE you compile poppler if you want background images generated
 * Install **poppler-data** if your want CJK support
* **fontforge** (with header files)
 * git version is recommended
 * In case you cannot compile with the official code, you may try [the `tmp` branch of my fork](https://github.com/coolwanglu/fontforge/tree/tmp)
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

 - Make sure poppler has been compiled with --enable-xpdf-headers
   - Especially when you see something about goo/GooString.h
 - Make sure C++11 is supported by your compiler
 - Fontforge has not been linking friendly until recent:
   - Git version is recommended
   - If there's something wrong about 'spiroentrypoints.h', install header files of libspiro
   - If there's something wrong about 'undefined reference of Py_xxx', install header files of python-2.x
   - If there's something wrong about 'libintl.h', install gettext and set your system include path accordingly.
