Crash means a bug. Unexpected visual results might be caused by wrong parameters, but program should never crash. This article describes how to extract useful information when pdf2htmlEX crashes, which would allow the developers to pinpoint and fix the issue much faster.

### Quick instruction for developers
- Double check the versions of pdf2htmlEX and libraries.
- Identify if the crash was caused by FontForge.
- If so, report to FontForge developers with relevant font files.
- Otherwise, create a new issues with relevant info.
- If you would like to create a stack dump, you need to build the debug version (see [Building](https://github.com/coolwanglu/pdf2htmlEX/wiki/Building)).

### Instructions for newcomers

The first thing to do is to make sure that the version of pdf2htmlEX and all depended libraries are fresh enough, as described in the [Building](https://github.com/coolwanglu/pdf2htmlEX/wiki/Building) page. Because bugs might have already been fixed in newer versions. **You need to tell the developers that you have verified this, by showing the result of `pdf2htlmEX -v`, or they will ask you to do so anyway before they can move forward**.

Whenever pdf2htmlEX crashes, run it again with the same arguments, except for an extra `--debug 1`, which tells pdf2htmlEX to show internal details which might reveal the cause. 

Here's a typical fraction of the messages, showing that pdf2htmlEX is trying to convert the 9th font found in the PDF file.
```
Embed font: /tmp/pdf2htmlEX-E36Cv0/f9.ttf 9
Add new temporary file: /tmp/pdf2htmlEX-E36Cv0/__raw_font_9.ttf
em size: 2048
Add new temporary file: /tmp/pdf2htmlEX-E36Cv0/f9.map
space width: 0.182
Add new temporary file: /tmp/pdf2htmlEX-E36Cv0/f9.woff
```

Most likely the crash happened when pdf2htmlEX was trying to convert a font file with FontForge. FontForge is one of the best free font manipulation tools out there. It might be actually more famous as a font editor, as it's usually used by font designers, who want to create and modify fonts using GUI, or doing automatic jobs using scripts. There are also interface exposed to communicate with the internals of FontForge, which is the way that pdf2htmlEX is using. Unfortunately, the interface is not well maintained, so I(Lu Wang) had been using it in a hacky way. 

Generally speaking there are three types of causes, in the order of likeliness.

- FontForge crashes when converting the files.
- The interface of FontForge is not correctly used by pdf2htmlEX.
- The font is obsolete or malformed.

You need to identify the cause, because each type is supposed to be fixed by different groups of people. To do so, pay attention to the last font mentioned in the message mentioned above. Suppose that the previous fraction is the last thing you saw before pdf2htmlEX crashed, you know that something might have went wrong when processing the 9th font. You may want to open the FontForge GUI, try each of the files mentioned there, and see if you can convert them into different types. In this example, you need to pay attention to the following files:

- /tmp/pdf2htmlEX-E36Cv0/f9.ttf
- /tmp/pdf2htmlEX-E36Cv0/__raw_font_9.ttf
- /tmp/pdf2htmlEX-E36Cv0/f9.woff

For each of them, open it in FontForge, and click the menu items: File -> Generate Fonts... -> Uncheck Validate Before Saving -> Generate. You might want to test different font formats, including the same format as the input file. (FontForge needs to parse the file even if you want to convert a ttf file into another ttf file).

If FontForge crashes, then it must be a bug of FontForge. Note exactly how you made FontForge crashes and submit it to FontForge developers with relevant files. Here's [an example](https://github.com/fontforge/fontforge/issues/873). Be polite and patient, as it might take tons of efforts before it can be fixed. When the issue has been fixed, update FontForge and pdf2htmlEX should then work smoothly.

If FontForge didn't crash no matter how you played with it, it's likely to be a bug of pdf2htmlEX. Now create an issue and tell the developers what you have tried.

The third type, where the input font file is obsolete, cannot be easily detected. It might cause both of the issues above. But if you see lots of warning messages printed by FontForge, complaining invalid numbers used in the font files, it might be the case. In this situation, you can still submit bugs to FontForge or pdf2htmlEX, but keep in mind that these are usually edge cases, which might require a long time to fix. The better thing to do might be to recheck the source of your PDF file and see if you can get a recent version. There used to be a dark era of PDF when the format was not mature, but it has been much better recently.

