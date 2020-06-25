### This page lists some common recipes of pdf2htmlEX

### First thing first
- It is highly recommended that you install `ttfautohint` and always add `--external-hint-tool=ttfautohint` to each of the following recipes. This tool enhances font rendering for all browsers on Windows.
- Double check you have `poppler-data` installed, for CJK characters.

  The current `pdf2htmlEX` has its own copy of `poppler-data` located in the directory
  `/usr/local/share/pdf2htmlEX/poppler`. You can provide your own copy by using `pdf2htmlEX`'s
  command line switch `--poppler-data-dir <pathToYourCopy>`.
- If you have compiled your own copy of `pdf2htmlEX`, double check you have run `sudo make install`, or pdf2htmlEX may not be executed correctly

### The simplest case
Suppose you have a PDF file `pdf/test.pdf`, simply running

    pdf2htmlEX --zoom 1.3 pdf/test.pdf

would produce a single HTML file `test.html` in the **current directory**.

### Advanced
 
    pdf2htmlEX -f 3 -l 5 --fit-width 1024 --bg-format jpg pdf/test.pdf

would convert only the 3rd, 4th and 5th pages, and fit the page width to 1024 pixels.
Background images will be generated in the JPEG format.

### For publishers

    pdf2htmlEX --embed cfijo --dest-dir out pdf/test.pdf

would produce a `test.html` and accompanying files in the `out` directory, in this way all the resources (fonts, images, css and javascript) are stored in separated files such that the viewer can take more advantage of browser caches.

### For advanced publishers

    pdf2htmlEX --embed cfijo --split-pages 1 --dest-dir out --page-filename test-%d.page pdf/test.pdf

would do something similar above, but each individual page is stored in a separated file. The files are named as `test-0.page`, `test-1.page` and so on, as specified in the command line. There is still a `test.html` which loads the pages dynamically through ajax. In this way the publishers are given full control, who can organize the pages as they like, for example, to implement lazy page loading.

### The Ultimate Hand

    pdf2htmlEX --fallback 1 pdf/test.pdf

would also produce a single `test.html`, which, however, consists of images and hidden text. This mode provides maximum accuracy and compatibility, at the cost of larger file size. Use this mode only when pdf2htmlEX cannot correctly process your files otherwise.

### More
Just remember `man pdf2htmlEX` and `pdf2htmlEX --help` are always your best friends.