# dummy

## Why I got compilation errors?
 
 - Make sure you have installed all required packages (and headers)
 - Make sure poppler has been compiled with --enable-xpdf-headers
   - Especially when you see something about goo/GooString.h
 - Make sure C++11 is supported by your compiler

## Why there is no image generated?

 - Make sure you did not specify --process-nontext 0
 - Make sure libpng (and headers) is installed BEFORE poppler was compiled.

## Why the generated HTML file looks ugly?

Recommended web browsers
 - IE9 / Chrome (Windows)
 - Firefox / Chrome (Linux/Mac)
 - Dolphin Browser (Android)

## Why I got incorrect text after copy & paste?

try run with --always-apply-tounicode 1

## Why the generated text is so small?

try run with --zoom 2

## Why images are blurred?

try run with --hdpi 288 --vdpi 288