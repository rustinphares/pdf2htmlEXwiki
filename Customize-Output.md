pdf2htmlEX allows you to customize the output as you like. 

The files telling pdf2htmlEX how to compose the output are stored in `data-dir`. Run `pdf2htmlEX -v` to find the default location, or you may specify a new one with the parameter `--data-dir`.

`data-dir/manifest` is the template for the output. A simple syntax is supported, which is explained in the deafult `manifest` file. You can add or remove HTML/CSS/JavaScript code here, or even change the entire layout.

By default the following files are used in `manifest`

- `base.css`: General CSS styles that do not depend on specific PDF files
- `jquery.css` : A copy of jQuery, required by `pdf2htmlEX.js`
- `pdf2htmlEX.js` : A simple UI implementation for demonstration purpose

The syntax of manifest is experimental, which might be changed in the future.