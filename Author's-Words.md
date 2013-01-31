pdf2htmlEX was first written as more-like-a-toy. 

When I heard about complains about no handy tools to present PDF documents online, from my friend Hongliang Tian, I replied without any thought "why not convert to HTML directly", and took that as a challenge. 

Hongliang wanted all text from PDF available on the web page. At that time he had made a poppler-based tool to produce PDF information in JSON, which can be further processed and rendered with Javascript. That's where I started to read poppler and PDF spec -- I knew nothing about them at that time.

Before long I realized that font is a big boss in the stage. Thanks to Fontforge I did't have to go too deep into the specification of TrueType (while still I have to read it once), but I had to learn about font from zero, and fight against the coding style (not bad, just unfamiliar) and bugs there.

The rest part was not so hard, as I've got a little background with C/C++/HTML/CSS/Javascript/Python. This is actually a good chance of thinking and comparing these languages together.

I'd like to thank Wanmin Liu for his help of testing and promoting this tool, and of course all the 
contributors to this one-man spare-time project. I'm quite happy to see that it's useful to others.

   
   
   
   


Lu Wang

2013.02.01