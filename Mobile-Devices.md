pdf2htmlEX does not official support mobile devices, mainly because the developers do not have enough time and resources to test on them.

Output of pdf2htmlEX may or may not run smoothly on your mobile devices, in case it does not, you might want to try one of the following tricks. They have been reported by individual users that might improve the performance for specific input, but they may break for others.

- In `share/base.css.in`, add `-webkit-overflow-scrolling: touch;` to `#page-container`.
- Hide pages that are out of screen using JavaScript, by completely removing them from the DOM.
- Trigger 3d acceleration using `translateZ` or `translate3d` CSS property.