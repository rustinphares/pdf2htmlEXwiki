pdf2htmlEX was first written as more-like-a-toy. 

When I heard about complains about no handy tools to present PDF documents online, from my friend Hongliang Tian, I replied without any thought, "why not convert to HTML directly", and took that as a challenge. 

Hongliang wanted all text from PDF available on the web page. At that time he had made a poppler-based tool to dump text information from PDF in JSON, which can be further processed and rendered by Javascript. That's where I started to read poppler and PDF spec -- I knew nothing about them at that time.

Before long I realized that font is a big boss in the stage. Thanks to Fontforge I did't have to go too deep into the the TrueType spec(while still I have to read it once), but still I had to learn about many things from zero, especially different font formats and encodings, and fight against the coding style (not bad, just unfamiliar) and bugs there. Right now, Fontforge has also become much more linking-friendly than before.

The rest parts were not so hard, as I've got a little background with C/C++/HTML/CSS/Javascript/Python. This is actually a good chance of thinking and comparing them together.

I'd like to thank Wanmin Liu for his help of testing and promoting this tool, and of course all the 
contributors to this one-man spare-time project. 

I'm quite happy to see that this piece of tool is useful for others.

Lu Wang   
2013.02.01