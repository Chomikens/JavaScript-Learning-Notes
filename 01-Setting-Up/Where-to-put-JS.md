
# Introduction to Script Loading Strategies in HTML

Choosing the right place to insert your JavaScript (`<script>`) tags in an HTML document is crucial for optimizing both the loading time and the performance of your website. The way a script is loaded can significantly impact the user's experience, affecting how quickly they can interact with your page. This guide explores three primary methods for loading scripts: using `async`, `defer`, attributes, and placing scripts just before the closing `</body>` tag.

## The Impact on Page Load Performance
The loading strategy you choose for your scripts affects the page's load time and rendering. Here's how:

-   ****Async****: The script with the async attribute is downloaded asynchronously in the background, at the same time as the rest of the HTML page is loaded. As soon as the script is downloaded, the browser stops loading the page and executes the script immediately. This means that the script can be executed before the entire page has finished loading, and the exact moment of execution depends on how fast it is downloaded
-   ****Defer****:  As with async, the script with the defer attribute is retrieved asynchronously, but its retrieval does not affect the page loading process. Scripts with the defer attribute are executed only after the HTML page is completely loaded, just before the DOMContentLoaded event. The scripts are executed in the order in which they appear in the document.
-   ****Before closing body tag****: Placing scripts just before the closing `</body>` tag is a traditional technique to ensure the DOM is fully loaded before script execution, but it doesn't offer the asynchronous loading benefits of async or defer. In modern web development, using async or defer is generally preferred over placing scripts at the end of the body, as they provide better control over script loading and execution without blocking the page rendering.

| Attribute | Load Time | Execution Time | Use Case |
|-----------|-----------|----------------|----------|
| Async | Asynchronously with HTML parsing | Immediately after download, pauses HTML [parsing](01-Setting-Up/FAQ-for-beginners/What-is-HTML-parsing.md) | Independent scripts, like analytics |
| Defer | Asynchronously with HTML parsing | After HTML parsing, before `DOMContentLoaded` event | Scripts that need the full DOM but no strict execution order |
| None (Before `</body>`) | After HTML parsing | Immediately after loading, just before `DOMContentLoaded` event | Scripts dependent on a fully parsed DOM |

## Example
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>I hope you have great day! </title>
    <link rel="stylesheet" href="style.css" type="text/css">
    <!--  Async-->
    <script src="./async.js" type="text/javascript"></script> 
    <!-- Defer -->
    <script src="./defer.js" type="text/javascript"></script>
</head>
```

  
