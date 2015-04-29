footer: Making Your Site Faster — Dan Barrett, 2015
slidenumbers: true
# Making Your Site Faster
### And helping out those with bad internet

#### <br /><br /><br />Dan Barrett — Web Developer, Humaan

---

## Current Statistics
- As of the 01/01/2015, the average page size for the Top 100 websites is 1343 KB
- Top 1000 is 1941 KB
- Mainly related to images or Flash

---

## [fit] What do these results say about page size?

---

## It tells us
- That the Top 100 sites have good developers

## We don't all do the same
- All sites on HTTP Archive on the 1st of April of this year average 1950 KB in size

<!-- maybe a graph for sizes over the years -->

---

## What should be done?
1. Minimise the amount of HTTP requests
2. Perform image compression
3. Minify content where possible
4. Strategic DOM manipulation
5. ???
6. Profit

<!-- fix this slide - it sucks -->

---

## Minimising HTTP Requests
- Each additional request adds downtimes due to DNS lookups and initiating a GET request for the file
- Most browsers allow a maximum of 8 concurrent requests per unique domain name (not IP address)
- Use sharding to split requests across the same IP address (but don't overdo it)
- Concatenate, but do it wisely

^ define what concatenate is

<!-- show chart of browser files being downloaded -->

---

## 2. Compress Images
- Images store unneeded comments, metadata colour profiles
- Use tools like ImageOptim, JPEGmini, and ImageAlpha
- Or use a cloud service like Kraken or EWWW IO

![inline](images/img_graph.png)

---

## 3. Minify Content
- Comments are great for the dev team, but not necessary for the world to see
- Changes variables from `aVeryImportantVarName` to `a` automatically
- Concatenate source files, but use CDNs for common frameworks/libraries (i.e. jQuery)

<!-- CDNs for common libs, but fallback to local if needs be -->

---

## 4. DOM Manipulation
- Writing to the DOM is slow!
- Ideally search using ID or tag selectors
- Use `<canvas>` xor React for crazy-fast performance
- Combine alterations to a node into one task (if possible) 

<!-- rewrite this page - remove canvas/React, remove alterations (as need to provide demo) -->

---

<!-- move the following 2 slides into their relevant sections -->

## 5. The Easy Stuff
- Put your `<script>` tags in the footer (or use magic)
- Load CSS asynchronously (e.g. Enhance.js, Yepnope, RequireJS, etc) to stop it blocking your page load
- Lazy load images so only images near the viewport are loaded

---

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
- Before optimisation took **~7.9ms** at minimum to complete and wrote to the DOM every time
- After optimisation... **~0.2ms** at minimum to complete and only touches the DOM when absolutely necessary

<!-- move this to the JS section -->

---

## The Takeaway

---

#### We can all make a difference
- Take the time to ensure your code isn’t writing to the DOM unnecessarily
- Use the Chrome DevTools to run tests and see how your code performs

<!-- show screenshot of DevTools -->

---

## The Future

### it all changes...

---

## HTTP/2

- Based on Googles SPDY protocol
- Lowers the cost of multiple requests
- Multiplexes, so can send and receive data at the same time
- Sprites, inlining, and sharding no longer necessary

---

## WebP & WebM

- WebP combines the best of both JPEG and PNGs
- WebM is a video container that can replace the need for gifs
- Codecs required are free and open-source

![inline](images/webp_graph.png)

---

## Thanks

### Questions?

#### Slides and Reading List:<br />[https://github.com/yesdevnull/Making-Your-Site-Faster](https://github.com/yesdevnull/Making-Your-Site-Faster)