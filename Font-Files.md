In this article we discuss about pitfalls and considerations regarding font files in PDF, while optimizing output of pdf2htmlEX.

### `pdffonts`
`pdffonts` is a handy tool supplied in the Poppler library. It shows the information of all the fonts used in a PDF file: name, type, encoding, embeded or not etc.

Here's a typical output of `pdffonts`.

```
name                                 type              encoding         emb sub uni object ID
------------------------------------ ----------------- ---------------- --- --- --- ---------
Arial,Bold                           TrueType          WinAnsi          no  no  no      19  0
Arial                                TrueType          WinAnsi          no  no  no      20  0
NWBJZL+NimbusRomNo9L-MediItal        Type 1            Custom           yes yes no      30  0
FCXRUF+NimbusRomNo9L-ReguItal        Type 1            Custom           yes yes no      33  0
FQDHWA+NimbusRomNo9L-Regu-Slant_167  Type 1            Custom           yes yes no      36  0
ZRUSRO+CMSY7                         Type 1            Custom           yes yes no      39  0
RBFYGC+Helvetica                     TrueType          MacRoman         yes yes no      48  0
TIVRUK+Helvetica-Bold                TrueType          MacRoman         yes yes no      49  0
NVCFEO+Calibri-Bold                  TrueType          WinAnsi          yes yes yes    127  0
ZBVPYI+Calibri-Bold                  TrueType          WinAnsi          yes yes yes    142  0
```

In this case, all fonts are embedded in the PDF font except for the two Arial ones.

### Embed or Not
One of the great features in PDF is that font files can be embedded into PDF files, such that the PDF file can be rendered correctly even if that font is not available in the viewer's machine. On the other hand, font files can also be referred as names, and the PDF viewer will try to find that font, or a closest match if not found, in the viewer's machine.

If you are familiar with fonts on the Web, it's roughly the same, font files can be embedded via `@font-face`, or just be referred to with names.

In the PDF specification, [14 standard fonts](http://en.wikipedia.org/wiki/Portable_Document_Format#Standard_Type_1_Fonts_.28Standard_14_Fonts.29) are supposed to be provided by any PDF viewer, so these fonts are often not embedded in order to save space. Some publishers/software choose not to embed some other font files assuming that all their viewers will have that font file installed. 

Note that there are no such standard fonts defined in the Web standards, although some fonts are indeed available on almost all machines.

If a font file is not embedded in the PDF file, yet it cannot be found in the viewer's machine (not even a close one), usually a fallback font will be used, which is likely to cause rendering issues. Therefore pdf2htmlEX always **embed matching fonts** in the output, even if this might increase the output size a lot.

The reason it has been designed so is that, consider which one is more important for a newbie user who has no idea about all the details, rendering or size? This behavior can be changed via the `--embed-external-font` option.