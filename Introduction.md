### pdf2htmlEX renders PDF files in HTML, accurately.

***

### Why HTML ?

PDF and HTML are quite different formats.
 - PDF focues on the capability of accurate representing and printing all kinds of documents.
 - HTML focues on multimedia, user interaction, network optimization.

What would you do if you want to show some PDF-quality contents online ?
 - [Lazy] To let user download or read with the plugin, which lead to terrible user experience.
 - [Easy] To convert PDF pages into images, then embed into HTML pages, which produces either blurred text or monster sized files/network cost. Also text are logically lost, readers cannot perform searching or copying.
 - [Clever] Still to convert PDF into images, but with hidden text layer and images with different resolutions. This is actually a pretty good solution (only) when you have powerful server and high-capacity networks.
 - [Good#1] To use Javascript to parse and render the PDF. Server is relieved, but all burden comes to the client-side, if you care.
 - [Good#2] To convert to HTML. One-time conversion, similar file size as the original PDF, preserved text, light weight for both server & client. Happy ending!

So you say "convert to HTML" is best, what there are still PDF files ?
 - No I didn't, I say "good" only. What I didn't say is that **all above but the last one** can support full PDF features. Because after all HTML and PDF are different formats, **there is no lossless conversion between them**.
 - However, HTML is capable enough most of the time. Because most PDF files are simple. Think about things that you have seen in PDF but never in HTML.

Finally, HTML+CSS+Javascript nowadays means nothing impossible. 
 - For providers: full control
   - Documents embedded with consistent theme and behavior with your own site.
   - Cross references to other documents, as simple as hyperlinks in HTML.
   - Access statistics, dynamic contents...
 - For readers: better experience
   - Read while downloading: just like old times (with HTML)
   - Plugin-free: No more ugly plugins!
   - Better UI, better integration = better website.

(much) easier & better than with PDF huh?

***

### What's special with pdf2htmlEX ?

Accuracy Text preservation.

If you are worried about misplaced text with ugly fonts, you must have tried to convert PDF files into HTML, desperately. Don't worry and take a look at the demo pages in the home page of pdf2htmlEX, which might be able to change your mind.

pdf2htmlEX was first designed especially for scientific papers, which contain different fonts and complicated formulas and figures.

Also Javascript is optional, the converted HTML file should work without Javascript.

***

### When/Who should use pdf2htmlEX ?

 - Online PDF preview services
 - Content providers: online newspapers, magazines, books ...
 - Personal: resumes, research papers ...
 - Create web pages with LaTeX !

