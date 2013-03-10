### This page lists some common recipes of pdf2htmlEX

### First thing first
- It is highly recommended that you install `ttfautohint` and always add `--external-hint-tool=ttfautohint` to each of the following recipes. This tool enhances font rendering for all browsers on Windows.
- Double check you have `poppler-data` installed, for CJK characters.
- Double check you have run `sudo make install`, or pdf2htmlEX may not be executed correctly

### The simplest case
Suppose you have a PDF file `pdf/test.pdf`, simply running

    pdf2htmlEX pdf/test.pdf

would produce a single HTML file `test.html` in the **current directory**.

### Advanced
 
    pdf2htmlEX -f 3 -l 5 --fit-width 1024 pdf/test.pdf

would convert only the 3rd, 4th and 5th pages, and fit the page width to 1024 pixels

### For publishers

    pdf2htmlEX --single-html 0 --dest-dir out pdf/test.pdf

would produce a `test.html` and accompanying files in the `out` directory, in this way all the resources (fonts, images, css and javascript) are stored in separated files such that the viewer can take more advantage of browser caches.

### For advanced publishers

    pdf2htmlEX --single-html 0 --split-pages 1 --dest-dir out pdf/test.pdf

would do something similar above, except for there is no `test.html`, but a series of files names as `test0.page`, `test1.page` and so on. Each `.page` file contains the a `<div>` element corresponding to a page, which gives the publisher full control. In this way a publisher can organize the pages as they like, and they can also implement lazy loading for pages.

### The Ultimate Hand

    pdf2htmlEX --fallback 1 pdf/test.pdf

would also produce a single `test.html`, which, however, consists of images and hidden text. This mode provides maximum accuracy and compatibility, at the cost of larger file size. Use this mode only when pdf2htmlEX cannot correctly process your files otherwise.

### More
Just remember `man pdf2htmlEX` and `pdf2htmlEX --help` are always your best friends.
