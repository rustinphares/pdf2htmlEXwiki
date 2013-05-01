The output of pdf2htmlEX is flexible, you can tweak it as you like.

The files telling pdf2htmlEX how to compose the output are stored in `data-dir`. Run `pdf2htmlEX -v` to find the default location, or you may specify a new one with the parameter `--data-dir`.

`data-dir/manifest` is the template for the output. A simple syntax is supported, which is explained in the default `manifest` file. By default the following files are used in `manifest`

- `base.css`: Essential CSS styles that do not depend on specific PDF files
- `fancy.css`: A default UI theme
- `jquery.css` : A copy of jQuery, required by `pdf2htmlEX.js`
- `pdf2htmlEX.js` : A simple UI implementation for demonstration purpose

You may modify `fancy.css` to change the UI appearance. You can even include your own CSS files after the `$css` line, in order to override styles defined in PDF!

Note that the syntax of manifest is experimental, which might be changed in the future.
