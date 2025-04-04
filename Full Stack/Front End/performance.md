Low Priority -
1. Preload URL's - Prefetch necessary resources to display web page in future.
2. CSS Concatenate - In HTTP/1 using plugins or online tool beefore or during build.
3. Remove Unused CSS Selectors using online tools.
4. Use WOFF 2.0 Web Font compression format
5. Preconnect fonts rather than parsing the CSS file and looking for font file from another server.
6. Keep web font size under 300kb
7. Prevent Flash Text until Font is loaded.
8. Check Dependency Size before choosing libraries.

Medium Priority -
1. Minify HTML - Remove comments, white spaces, new lines to reduce size and load time. NPM MOdules do the job.
2. Use CDN to serve static assets.
-> High performance DNS: Use DNS from third party providers like AWS, Google, Azure. Ensure high TTLs.
-> Move origin close to CDN to keep low latency.
-> Have IPv6 conncectivity.
3. Use Vector Images(SVG) rather than bitmap since they scale, and can be animated and modified by CSS.
4. Set Image Dimensions to reserve page space. This ensures page layout doesn't change during loading.
5. Avoid Base64 encoded images, which are directly embedded on HTML/CSS. This means it has to be re-downloaded every time page is loaded. Also not compatible with older versions. Referencing binary images that can be cached is  better.
6. Lazy Loading - Lighthouse identifies how many images are offscreen, which can be lazily loaded.
7. Responsive Images - Images served close to display size, using srcset and picture
8. Avoid multiple inline JavaScript, such as placing it inside <body> directly. Use external files under <head> with async to avoid blocking DOM.
9. Dependency Updates - Use most optimised code. Use npm-check to update libraries.
10. JavaScript Performance - Timeline tool in Chrome Developer evaluates scripts to find most time consuming ones.
11. Service Workers in PWA cache data, execute heavy tasks without impacting user experience.
12. Cookie Size doesn't exceed 4096 bytes, and domain name shouldn't have more than 20 cookies. Placed in HTTP headers, and can impact response time.

High Priority - 
1. Avoid iframes - bad for performance, accessibility, usability, and not indexed by search engines.
2. Minified CSS - Remove comments, whitespaces to lower bandwidth and resource usage.
3. Non-blocking CSS - preload will load the CSS files before the browser starts showing content of page. <link rel="preload" href="style.css" as="style" />
4. Inline Critical CSS - Collects above-the-fold CSS sufficient to help render the visible part of page. Embedded before principle CSS call.
5. But Avoid Inline CSS to decrease HTML flie size and load time.
6. Analyse StyleSheets Complexity - to reduce redundancies and validation errors, to let browser read them faster.
7. Images optimization - Use CSS3 effects, fonts instead of text encoded in image, SVG, TinyJPG.
8. Choose Image Format - Lighthouse helps choose modern formats.
9. Minify JavaScript - Space, comment, break to reduce size and speed up load times, lighten download.
10. Non-blocking JavaScript - When HTML Document is parsed and reaches "script" tag, it stops and runs it. Hence use async or defer before src to asynchronously run it.
11. Use HTTPs - "Lets Encrypt" provides SSL certificates to sites.
Otherwise modern browsers limit functionalities(APIs).
12. Page Weight - Less than 1500 KB,i.e., transfer size of all resource requested by page.
13. Page Load - To reduce bounce increase(lose user interest) < 3 seconds
14. Keep the Time to First Byte < 1.3 seconds
15. Minimize HTTP Requests - Combine files, caching, CDN and eliminate unnecessary resources.
16. Use same protocol for your site and site serving files.
17. Serve reachable files - 404 request can slow down the performance of your website and negatively impact the user experience.
18. HTTP Caching - Set HTTP headers to avoid expensive number of roundtrips between your browser and the server
