Mobile devices are not officially supported. There are so much different devices such that:

- The developers do not have enough time and resources to test on them.
- Sometimes the target devices are just too slow
  - It might be still fast enough to view PDF files and normal web pages, as the _viewers_ have been highly optimized, but usually the web browsers are not optimized for complicated web pages such as those produced by pdf2htmlEX.

Output of pdf2htmlEX may or may not run smoothly on your mobile devices, in case it does not, you might want to try one of the following tricks. They have been reported by individual users that might improve the performance for specific input, but they may break for others.

- In `share/base.css.in`, add `-webkit-overflow-scrolling: touch;` to `#page-container`.
- Hide pages that are out of screen using JavaScript, by completely removing them from the DOM.
- Trigger 3d acceleration using `translateZ` or `translate3d` CSS property.



### Survey
Please provide more info, for example `Most files of mine are slow on FOO devices/OSes but not BAR devices/OSes`. **Please confirm your result with at least 10 different files before posting**