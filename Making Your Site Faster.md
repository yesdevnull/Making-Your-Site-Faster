footer: Making Your Site Faster — Dan Barrett, 2015
slidenumbers: true
# Making Your Site Faster
## And helping out those with bad internet

#### Dan Barrett — Digital Developer, LivingBrand

---

## Current Statistics
- As of the 01/01/2015, the average page size for the Top 100 websites is 1448 KB[^1]
- Top 1000 is 1889 KB[^2]
- Related to JPEGs or Flash

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
- Minimise the amount of HTTP requests
- Perform image compression
- Minify content where possible
- Strategic DOM manipulation

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
- Comments are great for dev team, but not necessary for the world to see
- Change variables from `aVeryImportantVarName` to `a` automatically
- Concatenate source files, but use CDNs for common frameworks (i.e. jQuery[^9])

[^9]: [jQuery on Google CDN](https://developers.google.com/speed/libraries/devguide#jquery)

---

## 4. DOM Manipulation
- The DOM is slow!
- Ideally search using ID or tag selectors[^10] [^11]
- Use `<canvas>` xor React for crazy-fast performance[^12]
- Combine alterations to a node into one task (if possible)[^13]

[^10]: [Selector optimisation with 24 Ways](http://24ways.org/2011/your-jquery-now-with-less-suck)

[^11]: [10 performance tips from Paul Irish](http://jonraasch.com/blog/10-advanced-jquery-performance-tuning-tips-from-paul-irish)

[^12]: [Flipboard goes to 60](http://engineering.flipboard.com/2015/02/mobile-web/)

[^13]: [DOM node alterations](http://ejohn.org/blog/dom-documentfragments/)

---

## [fit] Is this practical to do in the real world?

---

# Yes!

---

## Personal Case Study #1
- Client with products page list - weighed in at **12.2 MB**
- Due to: no minification, bad use of images (600x600 scaled down to 200x200)
- After refactor: **2.5 MB** with optimised images and minified JS/CSS