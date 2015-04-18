footer: Making Your Site Faster — Dan Barrett, 2015
slidenumbers: true
# Making Your Site Faster
## And helping out those with bad internet

#### Dan Barrett — Web Developer, Humaan

---

## Current Statistics
- As of the 01/01/2015, the average page size for the Top 100 websites is 1448 KB
- Top 1000 is 1889 KB
- Mainly related to images or Flash

---

## [fit] What do these results say about pagesize?

---

## It tells us
- That the Top 100 sites have good developers

## We don't all do the same
- All sites on HTTP Archive on the 1st of January of this year average 1931 KB in size

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
- Use tools like ImageOptim, JPEGmini, and ImageAlpha
- Or use a cloud service like Kraken or EWWW IO
- Responsibly serving images can save milliseconds and make the user happier

---

## 3. Minify Content
- Comments are great for the dev team, but not necessary for the world to see
- Changes variables from `aVeryImportantVarName` to `a` automatically
- Concatenate source files, but use CDNs for common frameworks/libraries (i.e. jQuery)

---

## 4. DOM Manipulation
- Writing to the DOM is slow!
- Ideally search using ID or tag selectors
- Use `<canvas>` xor React for crazy-fast performance
- Combine alterations to a node into one task (if possible)

---

## 5. The Easy Stuff
- Put your `<script>` tags in the footer (or use magic)
- Load CSS asynchronously (e.g. Enhance.js, Yepnope, RequireJS, etc) to stop it blocking your page load
- Lazy load images so only images near the viewport are loaded

—

## 5. The Easy Stuff (_cont…_)
- Use JPEGs for photos, not PNGs (surprising how often people stuff this up)
- Better yet, use the power of responsive images with `<picture>` or `<img>` on steroids (polyfill available)
- Use CSS sprites for icons (or SVG sprites or icon fonts)

---

## [fit]Care About Your Users

—

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
- JavaScript function polled every 100ms on `scroll` and `resize` events
- Before optimisation took **~7.9ms** to complete and wrote to the DOM every time
- After optimisation... **~0.2ms** to complete and only touches the DOM when absolutely necessary

—

## The Takeaway

—

#### We can all make a difference
- Take the time to ensure your code isn’t writing to the DOM unnecessarily
- Use the Chrome DevTools to run tests and see how your code performs

—

## Thanks

### Questions?

### Slides and Reading List: [https://github.com/yesdevnull/Making-Your-Site-Faster](https://github.com/yesdevnull/Making-Your-Site-Faster)