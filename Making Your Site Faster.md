footer: Making Your Site Faster — Dan Barrett, 2015
slidenumbers: true
# Making Your Site Faster
## And helping out those with bad internet

#### Dan Barrett — Digital Developer, LivingBrand

---

## Current Statistics
- As of the 01/01/2015, the average page size for the Top 100 websites is 1448 KB[^1]
- Top 1000 is 1889 KB[^2]
- Mainly related to images or Flash

[^1]: [HTTP Archive: Top 100](http://httparchive.org/interesting.php?a=All&l=Jan%201%202015&s=Top100)

[^2]: [HTTP Archive: Top 1000](http://httparchive.org/interesting.php?a=All&l=Jan%201%202015&s=Top1000)

---

## [fit] What do these results say about pagesize?

---

## It tells us
- That the Top 100 sites have good developers

## We don't all do the same
- All sites on HTTP Archive on the 1st of January of this year average 1931 KB in size[^3]

[^3]: [HTTP Archive: All](http://httparchive.org/interesting.php?a=All&l=Jan%201%202015&s=All)

---

## What should be done?
1. Minimise the amount of HTTP requests
2. Perform image compression
3. Minify content where possible
4. Strategic DOM manipulation
5. ???
6. Profit

---

## 1. Minimise HTTP Requests
- Each additional request adds downtimes due to DNS lookups and initiating a GET request for the file
- Most browsers allow a maximum of 8 concurrent requests per unique domain name (not IP address, so use those CNAMEs)
- Concatenate, but do it wisely

---

## 2. Compress Images
- Images store unneeded comments, extra metadata colour profiles
- Use tools like ImageOptim[^4], JPEGmini[^5], and ImageAlpha[^6]
- Or use a cloud service like Kraken[^7] or EWWW IO[^8]
- Responsibly serving images can save milliseconds and make the user happier

[^4]: [ImageOptim](https://imageoptim.com/)

[^5]: [JPEGmini](http://www.jpegmini.com/)

[^6]: [ImageAlpha](http://pngmini.com/)

[^7]: [Kraken](https://kraken.io/)

[^8]: [EWWW IO](http://ewww.io/)

---

## 3. Minify Content
- Comments are great for the dev team, but not necessary for the world to see
- Changes variables from `aVeryImportantVarName` to `a` automatically
- Concatenate source files, but use CDNs for common frameworks/libraries (i.e. jQuery[^9])[^10]

[^9]: [jQuery on Google CDN](https://developers.google.com/speed/libraries/devguide#jquery)

[^10]: [Letting Google host jQuery for you](http://encosia.com/3-reasons-why-you-should-let-google-host-jquery-for-you/)

---

## 4. DOM Manipulation
- Writing to the DOM is slow!
- Ideally search using ID or tag selectors[^11] [^12]
- Use `<canvas>` xor React for crazy-fast performance[^13]
- Combine alterations to a node into one task (if possible)[^14]

[^11]: [Selector optimisation with 24 Ways](http://24ways.org/2011/your-jquery-now-with-less-suck)

[^12]: [10 performance tips from Paul Irish](http://jonraasch.com/blog/10-advanced-jquery-performance-tuning-tips-from-paul-irish)

[^13]: [Flipboard goes to 60](http://engineering.flipboard.com/2015/02/mobile-web/)

[^14]: [DOM node alterations](http://ejohn.org/blog/dom-documentfragments/)

---

## 5. The Easy Stuff
- Put your `<script>` tags in the footer (or use magic)[^15]
- Load CSS asynchronously (e.g. Enhance.js[^16], Yepnope[^17], RequireJS[^18], etc) to stop it blocking your page load
- Lazy load images so only images near the viewport are loaded[^19]

[^15]: [The murky waters of script loading](http://www.html5rocks.com/en/tutorials/speed/script-loading/)

[^16]: [Enhance.js on GitHub](https://github.com/filamentgroup/enhance)

[^17]: [Yepnope](http://yepnopejs.com/)

[^18]: [RequireJS](http://requirejs.org/)

[^19]: [lazysizes image loader](https://github.com/aFarkas/lazysizes)

—

## 5. The Easy Stuff (_cont…_)
- Use JPEGs for photos, not PNGs (surprising how often people stuff this up)

---

## [fit] Is this practical to do in the real world?

---

# Yes!

---

## Personal Case Study #1
- Client with products page list - weighed in at **12.2 MB**, very slow to render
- Due to: no concatenation & minification, bad use of images (600x600 scaled down to 200x200), dead/poorly written code
- After refactor: **2.5 MB** with optimised images and minified JS/CSS (with no dead code)

---

## Personal Case Study #2
- JavaScript function polled every 100ms[^20] on `scroll` and `resize` events
- Before optimisation took **~7.9ms** to complete and wrote to the DOM every time
- After optimisation... **~0.2ms** to complete and only touches the DOM when absolutely necessary

<!-- put in Gist links -->

[^20]: [_.throttle by Underscore JS](http://underscorejs.org/#throttle)

—

## The Takeaway

—

#### We can all make a difference
- Take the time to ensure your code isn’t writing to the DOM unnecessarily
- Use the Chrome DevTools[^21] to run tests and see how your code performs[^22]

[^21]: [Chrome DevTools Page](https://developer.chrome.com/devtools)

[^22]: [Discover DevTools course](http://discover-devtools.codeschool.com/)