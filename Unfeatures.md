[Unfeatures](http://fluxbb.org/docs/unfeatures) are those not included intendedly. For example, you may not expect a JPG-to-PNG conversion tool would be able to retouch the images for you.

pdf2htmlEX is also a conversion tool, the target is to convert a PDF file into a Hi-Fi HTML file. Below there are a few features listed, which are either "won't be included" or "which I won't implement". Hopefully these will help shaping the scope of pdf2htmlEX.

### PDF manipulation and optimization
If something can be done by a PDF optimization tool, probably pdf2htmlEX won't do that. For example:
 - PDF linearization
 - Font optimization
 - Image optimization

Google `pdf manipulation tool` for more info.

However, pdf2htmlEX will handle those things caused by the differences between the formats of PDF and HTML, or those generated by pdf2htmlEX. For example:
 - Rasterization of PDF drawings and optimization of the rasterized images.
 - Page scaling
 - Text optimization (merging words etc)

### UI
You expect UI features of PDF viewers, but you should not expect UI features of PDF files. Likewise, I will try to define useful JavaScript functions for an easier handling of the contents, but I will not add UI controls (buttons, toolbars) in the HTML output.