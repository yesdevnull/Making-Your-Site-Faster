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

---

## 1. Minimise HTTP requests
- Each additional request adds downtimes due to DNS lookups and initiating a GET request for the file
- Most browsers allow a maximum of 8 concurrent requests per unique domain name

---

## 2. Compress images
- Images store unneeded comments, extra metadata colour profiles
- Use tools like ImageOptim[^4], JPEGmini[^5], and ImageAlpha[^6]
- Or use a cloud service like Kraken[^7] or EWWW IO[^8]

[^4]: [ImageOptim](https://imageoptim.com/) 
[^5]: [JPEGmini](http://www.jpegmini.com/)
[^6]: [ImageAlpha](http://pngmini.com/)
[^7]: [Kraken](https://kraken.io/)
[^8]: [EWWW IO](http://ewww.io/)

---

