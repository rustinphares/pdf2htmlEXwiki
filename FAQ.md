# dummy

## Why did you start this project?

 - For FUN

## What's the ultimate goal of pdf2htmlEX?

 - To make me happy
 - To be possibly useful for others

## pdf2htmlEX is really great! What shall I do?

 - Add a star in the [project page](http://github.com/coolwanglu/pdf2htmlEX), at the top-right corner.
 - Tell others about it, using your social power.
 - Use it and enjoy it.

## pdf2htmlEX sucks! What shall I do?

 - Tell me what's wrong.
 - Technical complaints are welcome.

## pdf2htmlEX doesn't work for my pdf!

 - Bug reports are always welcome, please file an issue with the link to the broken pdf file.
 - However there are several exceptions when the bug cannot be fixed in time (or at all)
   - PDF does not follow the standard (it might still be displayed correctly in PDF viewers)
   - It's actually something wrong with libraries used by pdf2htmlEX (poppler / fontforge)

## How about feature requests?

  - Keep in mind that pdf2htmlEX has been provided as a toy for hackers, not a user-friendly tool.
  - Patches are as welcome as bug reports.
  - I'll put into my TODO list those requests I found attractive/challenging/important.
   - There's little chance that feature requests about user interface will be accepted.

## Why I got compilation errors?

 - Make sure you have installed all required packages (and headers).
 - Make sure poppler has been compiled with --enable-xpdf-headers
   - Especially when you see something about goo/GooString.h
 - Make sure C++11 is supported by your compiler
 - If there's something wrong about 'spiroentrypoints.h', install header files of libspiro
 - If there's something wrong about 'undefined reference of Py_xxx', install header files of python-2.x

## 'Cannot open the manifest file'
 - Run 'sudo make install' or 'make install', depending on your environment.

## Why there is no image generated?

 - Make sure you did not specify --process-nontext 0
 - Make sure libpng (and headers) is installed BEFORE poppler was compiled.

## Why the generated HTML file looks ugly?

Recommended web browsers
 - IE9 / Opera / Chrome (Windows)
 - Firefox / Chrome / Opera (Linux/Mac)
 - Dolphin Browser (Android)

## Why I got incorrect text after copy & paste?

try run with --tounicode 1

## Why the generated text is so small?

try run with --zoom 2

## Why images are blurred?

try run with --hdpi 288 --vdpi 288