Here are a few tips on optimizations when using pdf2htmlEX or deploying HTML files produced by pdf2htmlEX.

## Static Resource Files

Some resource files used by pdf2htmlEX are static, for example `base.css`, `fancy.css`, `jquery.js` and `pdf2htmlEX.js`. You can store them on unique locations on your server, and refer them in `manifest`. Especially, you may link to jQuery from one of its CDN's.

This is very useful when a lot of HTML files are published: files become smaller, and clients can be benefited from the static URLs -- each file is downloaded only once and will be cached. 

## To Embed or Not to Embed

Resource files can be embedded into the HTML file via Data URI Scheme, or they can be stored separately. The behaviour can be tweaked via the `--embed` option. Embedding files into HTML will save HTTP requests, at the cost of 1/3 extra space due to the base64 encoding. Publishers should tweak the options carefully based on the actually file sizes and target network environments.

## Enable HTTP Compression

HTML file produced by pdf2htmlEX are often slightly larger than the original PDF file. One reason is that PDF has built-in compression support while HTML does not. This can be compensated by enabling HTTP compression on your HTTP server, often gzipped-HTML is smaller than the original PDF.