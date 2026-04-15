# Top 30+ JavaScript Frontend Interview Questions

**1. What are Preload, Reconnect, Prefetch, and Prerender?**
These are resource hints: `preload` fetches critical assets early, `preconnect` resolves DNS/TCP connections ahead of time, `prefetch` loads low-priority assets for future navigation, and `prerender` loads an entire page in the background.

**2. How can you do caching on a website?**
Caching can be implemented at the network level using HTTP cache headers (Cache-Control, ETag), or locally using Service Workers and browser storage APIs like LocalStorage and IndexedDB.

**3. What are ETag, Cache-Control, and Document Fragment?**
`ETag` validates if a cached file has changed, while `Cache-Control` sets caching durations and rules. A `DocumentFragment` is a lightweight, off-DOM container used to batch DOM insertions efficiently without triggering layout reflows.

**4. How do you optimize assets? What is image compression? What’s the difference between WebP, PNG, and JPG?**
Assets are optimized via minification, bundling, and Gzip/Brotli compression. WebP offers superior compression for the web, PNG allows for lossless quality and transparent backgrounds, and JPG is a lossy format best suited for complex photographs.

**5. What is a Memory Leak?**
A memory leak occurs when unused memory is not released by the garbage collector, often caused by forgotten `setInterval` timers, unhandled closures, or detached DOM elements.

**6. What’s the difference between Repaint and Reflow?**
A reflow recalculates the layout and positions of elements (which is computationally expensive), whereas a repaint only updates visual styles like color or visibility without affecting the layout.

**7. If a user clicks a button multiple times to fetch data, how to cancel old API calls?**
You can use the `AbortController` API, passing its signal to the `fetch` request and calling `abort()` before initiating a new request to cancel any pending network calls.

**8. Does React use Promise.allSettled() for parallel API calls? How does that work internally?**
React itself does not dictate data fetching methods, but developers often use `Promise.allSettled()` to execute multiple promises concurrently, resolving an array of outcomes regardless of individual promise rejections.

**9. What algorithm does Array.prototype.sort() use? What’s the output of [1, null, 5, 2, undefined]?**
Modern V8 engines use Timsort (a hybrid of merge and insertion sort). The output is `[1, 2, 5, null, undefined]` because elements are cast to strings for comparison ("null" comes after numbers), and `undefined` is always sorted to the very end.

**10. What happens when we hit a URL in the browser? What is CRP (Critical Rendering Path)?**
The browser resolves the DNS, establishes a TCP/TLS connection, fetches the HTML document, and parses it to build the DOM and CSSOM trees. These trees combine to form the Render Tree (the CRP) which dictates layout and painting.

**11. What events can we use when a website is loading?**
Key events include `DOMContentLoaded` (fired when the HTML is parsed and DOM is built) and `load` (fired when all external resources like images and stylesheets have finished downloading).

**12. Difference between Prototypal and Classical Inheritance in JavaScript**
Prototypal inheritance links objects directly to other objects via the prototype chain to share behavior, whereas classical inheritance uses structural blueprints (classes) to instantiate new objects.

**13. How does JavaScript handle asynchronous operations?**
JavaScript handles concurrency using a single-threaded Event Loop, offloading asynchronous tasks to Web APIs and queuing their callbacks in the task/microtask queues to be executed once the call stack is clear.

**14. What are the SOLID Principles?**
These are five design principles (Single Responsibility, Open-Closed, Liskov Substitution, Interface Segregation, Dependency Inversion) aimed at making object-oriented software more modular, scalable, and maintainable.

**15. How do we use OOP in JavaScript?**
OOP is implemented using the ES6 `class` syntax, constructor functions, `this` context binding, and the prototype chain to achieve encapsulation, inheritance, and polymorphism.

**16. What are Semantic HTML Elements?**
Semantic elements (like `<article>`, `<header>`, `<nav>`, `<main>`) clearly convey the meaning and structure of the content to both the browser and assistive technologies like screen readers.

**17. What is srcset in HTML?**
The `srcset` attribute on the `<img>` tag allows the browser to automatically select and download the most appropriate image resolution based on the user's device screen density and viewport width.

**18. Difference between display: none and visibility: hidden**
`display: none` completely removes the element from the document flow, reclaiming its space, while `visibility: hidden` makes the element visually invisible but retains its physical space in the layout.

**19. Basic performance-related common questions.**
Common strategies involve minimizing HTTP requests, implementing code-splitting, lazy-loading images, deferring render-blocking scripts, and optimizing the Critical Rendering Path.

**20. What is the use of the new operator in JavaScript?**
The `new` operator creates a blank, plain JavaScript object, links it to the constructor function's prototype, binds `this` to the newly created object, and returns the object.

**21. Explain the webpack build process?**
Webpack starts at an entry point, traverses `import` statements to build a dependency graph, applies specific loaders to transpile files (like JSX or Sass), and bundles them into optimized output files.

**22. How would you architect an application to support multiple devices?**
I would utilize a mobile-first responsive design strategy using CSS media queries and fluid grids, combined with responsive image techniques (`srcset`), and optimize touch interactions.

**23. What is the use of Headers in HTTP requests?**
Headers pass crucial metadata between the client and server, communicating information such as payload content types, authentication tokens, caching policies, and CORS configurations.

**24. What are render-blocking resources?**
These are external CSS files and synchronous JavaScript scripts in the `<head>` of a document that force the browser to pause parsing the HTML, delaying the initial paint of the page.

**25. Event Capturing vs Delegation vs Bubbling**
Events trickle down from the window to the target (capturing), fire on the target, and then bubble back up to the window (bubbling). Delegation takes advantage of bubbling by placing a single event listener on a parent element to manage its children.

**26. Can we bind this in an arrow function? What happens if we use the new operator with an arrow function?**
No, arrow functions lexically bind `this` from their surrounding scope and cannot be rebound using `call`, `apply`, or `bind`. Using `new` throws a TypeError because arrow functions lack an internal `[[Construct]]` method.

**27. Difference between map and object in JavaScript**
A `Map` allows keys of any data type, maintains exact insertion order, and is easily iterable. An `Object` only accepts strings or symbols as keys and doesn't guarantee strict iteration order for properties.

**28. What are Closure, Event Loop, Hoisting, and Currying?**
A closure retains access to outer scope variables; the Event Loop manages asynchronous queues; Hoisting elevates declarations to the top of their scope; Currying transforms a multi-argument function into a chain of single-argument functions.

**29. What are Web Core Vitals? How to improve them?**
Web Core Vitals are Google metrics measuring UX: LCP (loading speed), INP/FID (interactivity), and CLS (visual stability). Improve them by optimizing images, deferring scripts, and providing explicit dimensions for media.

**30. Explain Web Performance Metrics**
These metrics evaluate site speed and usability, including Time to First Byte (TTFB), First Contentful Paint (FCP), Largest Contentful Paint (LCP), and Total Blocking Time (TBT).

### Bonus Questions

**1. What are Symbols and Generators?**
`Symbol` is a primitive type that creates unique, immutable identifiers (often used to prevent object key collisions). Generators (`function*`) are special functions that can pause and resume their execution using the `yield` keyword.

**2. What are Web Components, Service Worker, Web Worker, and Progressive Web App (PWA)?**
Web Components allow for custom, reusable, encapsulated HTML tags. Service Workers manage offline caching and push notifications. Web Workers run heavy background scripts off the main thread. PWAs combine these technologies to deliver native app-like experiences on the web.

#### Answers created Using Gemini Pro. 
#### Many thanks to Gourav for sharing the questions.
