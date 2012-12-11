**Reflowable** means text can be automatically adapted to different output device, especially different widths. See [Wikipedia Page](http://en.wikipedia.org/wiki/Reflowable_document)

PDF is mainly designed for printing, where it is not necessary for text to be reflowable. Some PDF files with tags are reflowable, which is not common, and is not widely supported by PDF viewers. However HTML originated from reflowable plain text, although nowadays HTML pages become more and more complicated, large paragraphs of text are still reflowable -- unless for the purpose of obscure or encryption.

This page discusses about the difficulties to let pdf2htmlEX produce reflowable text in HTML from a PDF.

## Base Case

Each line is a box. If two lines l1 and l2 share the same left and right edges, l2 is exactly underneath l1 (touching vertically) and there is only one font appearing in both of them, we can append the text in l2 to l1, and increase the height of l1 by the height of l2, after that we remove l2.

For text in English, if l1 ends with a '-', we may need to remove it, otherwise we may need to insert a ' ' there.

## Left & Right Edges

 - Often the first line of a paragraph is indented, so now l1 and l2 does not have the same left edges. To merge them, we need to prepend some space to l1, either with space characters or a block with absolute width.
 - The last line of a paragraph is usually shorter than others, so now the right edges are different. No special treatment for output though.
 - In bulleted list and numbered list, the bullets/numbers may be consider as a part of the first line of the text, when the line is too long, the second line (and all later lines for the same item) will be indented (well, THIS LINE should be an example). To distinguish such lists from "a normal line followed by an indented paragraph", we need to recognize bullets and numbers, which sounds annoying.

## Line height

In HTML files produced by pdf2htmlEX, The position of a line is determined by the position of the top-left corner and the height of the line. Especially a correct height is necessary, because of the difference of the coordinate systems between PDF (origin point of characters) and HTML (bounding boxes).

The height of a line is determined by the tallest character in the lines regarding font families and sizes:

 - The line "acegmnopqrsuvwxyz" is shorter than the line "bdfhijklt"
 - There can be different font families, sizes, superscripts and subscripts.

So the height will be quite likely to change if the text is reflowed.

## Text That Should Not Be Reflowed

Underlined text in PDF may be actually normal text with a correctly positioned horizontal bar. Reflowing text is likely to break this combination. The cause of this is that some information cannot be recognized by pdf2htmlEX. 

Other similar things includes code blocks, math formulas (with symbols like square root or fractions with a horizontal bar), poems...

However these may not be easily recognized.

