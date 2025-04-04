# Internet

## Internet Protocol Suite (TCP/IP)
- Computers and servers communicate via protocols.
- Data is broken into packets and routed using IP.
- Packets travel via optic cables, satellites, wireless networks.
- TCP ensures delivery and reassembly.
- DNS translates human-readable website names to IP addresses and vice versa.

## HTTP
- Foundation of data communication on the WWW.
- Application-layer protocol defining message formatting and transmission between client (browser) and server.
- Stateless.

## Domain Name
- Human-readable address for computers to locate web servers.
- Second-level domain (website name) and top-level domain (.org, .com) registered through domain registrars.

## Hosting
- Service that allows websites to be placed on the Internet.
- **Shared Hosting** - Multiple sites share resources.
- **Dedicated Hosting** - One client uses an entire server.
- Other types: **Virtual Private Server (VPS), Cloud Hosting, WordPress Hosting**.
- Web hosts provide domain registration, SSL certificates, and support.

## DNS (Domain Name System)
- Hierarchical decentralized naming system/directory service.
- Tree structure with root servers, top-level domain servers, authoritative name servers, local DNS servers.

## Browsers
- Software application for displaying web pages.
- Single-threaded.

## Webpage Navigation Process
1. User enters URL.
2. Browser performs DNS lookup to get IP address.
3. TCP three-way handshake with the server over HTTPS.
4. TLS negotiation encrypts the communication.
5. Server responds with HTML.
6. TCP slow start algorithm prevents congestion.
7. Browser parses HTML into a DOM tree.

# HTML Basics

## Semantic HTML
- Using markup to reinforce content meaning.
- Improves accessibility, SEO, and readability.
- Example: `<header>`, `<nav>`, `<main>`.

## Forms and Validations
- Submit data to server in correct format.
- Client-side validation ensures correct input before submission.

## Accessibility
- Designing websites usable for everyone.
- Best practices: Image alternatives, keyboard navigation, color contrast.

## SEO Basics
- Improve search engine visibility and ranking.
- Use relevant content, keywords, meta tags, mobile-friendliness, fast loading speeds, and responsive design.

# CSS (Cascading Style Sheets)

## Styling HTML Documents
- Selectors target elements for styling.
- Responsive design via media queries.

## CSS Key Concepts
- **Cascade** - Top-down application of styles.
- **Inheritance** - Some properties (e.g., color, font-family) are inherited.
- **Specificity** - Determines which style rule is applied.
- **Importance** - Overrides other rules.

## Making Layouts
- **Flexbox** - 1D layout for flexible alignment.
- **CSS Grid** - 2D layout for more control.
- **Responsive Design** - Adapt content dynamically.
- **CSS Frameworks** - Bootstrap, Tailwind for rapid development.

## Responsive Web Design
- Uses fluid grids, flexible images, and media queries.

# JavaScript

## Overview
- High-level, interpreted programming language.
- Dynamically typed, prototype-based OOP.
- ECMAScript standard updates.
- Adds interactivity to web pages.

## DOM Manipulation
- The Document Object Model (DOM) provides methods and properties for interacting with HTML/XML.

## Fetch API
- Modern JavaScript interface for making HTTP requests.
- Uses Promises for async handling.
- Supports request cancellation and streamed responses.

# Version Control Systems (VCS)

## Overview
- Tools for tracking and managing code changes.
- Supports collaboration, history tracking, branching, merging.
- Example: **Git** (Distributed VCS for non-linear development).

## VCS Hosting
- Platforms for managing repositories with additional services like issue tracking and CI/CD.
- Examples: **GitHub, GitLab**.

# Package Managers

## Overview
- Automate installation, configuration, and removal of software packages.
- Handle dependency resolution and version management.
- Examples:
  - `npm`, `pnpm` - JavaScript package managers.
  - `pip` - Python package manager.

# Frameworks

## Choosing a Framework
- Web applications use frameworks for structured development.
- Example: **React** (Component-based UI library for JavaScript).

# Modern CSS

## Responsive Design Techniques
- **Media queries** for dynamic layouts.
- **Fluid typography** for better scaling.

## CSS-in-JS & Utility-first Frameworks
- **Tailwind CSS** - Utility-based design system with predefined classes for rapid development.

# CSS Architecture

## Methodologies
1. **Naming Conventions** - BEM (Block Element Modifier), SMACSS, OOCSS.
2. **Component-Based Design** - Modular styling.
3. **Separation of Concerns** - Maintainable code structure.
4. **Preprocessors** - Sass, Less for improved styling.
5. **CSS Modules & Utility Classes** - Scoped styles and reusability.

# CSS Preprocessors
- **Sass (Syntactically Awesome Stylesheets)**
- Features: Variables, nesting, functions, inline imports, math operations.

# Build Tools

## Overview
- Automate building applications from source code.
- Handle compiling (Babel), linking, minifying, and bundling (Webpack).
- Other tools: Gradle, Maven for Java.
- Optimize production output with parallel processing.

## Linters & Formatters
- Tools to enforce code quality and consistency.
Analyse source code for errors, bugs, etc, and enforce custom rules. Formatters restructure code to that style, such as indentation, linebreaks, spacing. Help reduce cognitive load on developers during code reviews. ESLint for JavaScript and Prettier for code formatting.
1. Prettier - Parses code and reprints with own rules. Run as part of development, or pre-commit hooks.
2. ESLint - Open-source static code analysis tool to identify JS code problems. Configurable and enforces coding standards.

## Module Bundlers - 
Dev tools that combine JS files and dependencies into single file for web browsers. Support code splitting, lazy loading, manage dependencies, optimize code etc. Transpile JS code, integrate with task runners.
1. Webpack - Transform, bundle or package resources with dependencies into static assets. Loaders preprocess files and plugins for optimization. Hot module replacement(replace module without state change) helps faster development and remove unused code.

Testing - Systematically evaluate software to meet requirements.
Unit testing: Verifying individual components or functions
Integration testing: Checking interactions between different parts of the app
Functional testing: Ensuring the app meets specified requirements
UI/UX testing: Evaluating the user interface and experience
Performance testing: Assessing app speed, responsiveness, and stability
Security testing: Identifying vulnerabilities and ensuring data protection
Accessibility testing: Verifying usability for people with disabilities
Compatibility testing: Checking functionality across different devices and platforms
Test-driven development(TDD) and Behavior-driven development(BDD)
1. Jest - Facebook created this testing framework. Automatic mocking, snapshot testing. Supports synchronous and asynchronous code. Built-in assertion library and test runner makes it easy to run tests in parallel.
2. Playwright - Open-source automation framework by Microsoft. Single API to automate Chromium browsers across OS. Supports multiple languages too, and has features such as auto-waiting, network interception and mobile emulation. Wait for dynamic content, cross-browser and cross-platform capabilities.

Authentication Strategies -
1. Basic Authentication: Client request URL, Server check Request Authorization header with username and password. If not found, sends www-authenticate: Basic realm response. User submites request after base64 encoding them in Authorization header.
2. Session Based Authentication: Client requests URL, Server validates credentials, creates session and stores in memory, which is also returned to client. Client stores it in cookie. Any requests henceforth sent with session ID.
3. Token based Authentication: Client requests URL, Server validates credentials, creates tokens and returns to client. Client stores in cookie/local storage. Any requests henceforth sent with token. Stateless since server doesn't store it. Random string signed with secret and has expiry.
4. JWT or JSON Web Tokens - Self contained and carries data. Carried on header to server. Contains header(base64 encoded token metadata).payload(base64 encoded data/claims).signature(created by hashing header and payload with secret)
5. OAuth - Open protocol for Authorization. Third party credited by application helps authenticate. Its types -
a. Autorization Code Grant Flow: Client_id(username), client_secret(password) are validated at Authorization_server. If user gives client app consent to receive code for scopes, it then sends token request.
b. Implicit Grant Flow: Skips authorization code, directly token.
c. Client Credential Grant Flow: No user interaction. Direct toekn request from Client App.
d. Password Grant Flow: User enters credentials owned by authorization server and requests token.
6. SSO - User logs in with single username and password to several related services.
7. SAML - Security Assertion Markup language. Identity Provider sends SAML assertion (XML Document with authorization information agreed upon and signed for trust) to User on authentication that sends it to Service Provider. Only then Session started.

Web Security Knowledge - Practices to protect websites from cyber threats.
1. HTTPS and TLS for secure data transmission
2. Cross-Site Scripting(XSS) prevention.
3. SQL injection protection
4. Cross-Site Request Forgery (CSRF) mitigation
5. Content Security Policy (CSP) implementation
6. Secure authentication and session management
7. Input validation and sanitization
8. Protection against clickjacking
9. Secure cookie handling
10. Regular security updates and patch management

1. CORS(Cross-Origin Resource Sharing) is a security mechanism to control access of resource from webpage in another domain. Request browser sends preflight request to server hosting the resource, and gets header response indicating if allowed.
2. HTTPS - Transport Layer Security ensures communication using asymmetric public key infra. Uses port 443, unlike HTTP 80. Send TLS Certificate with public key to start secure session, called TLS Handshake.
3. Content Security Policy - Helps prevent Cross-site scripting(XSS). Web developers specify sources of content which can be trusted and loaded. Implemented via HTTP headers or meta tags. Needs balance between security and functionality in case of third-party resources.
4. OWASP Security Risks - Open Web Application Security Project identifies and ranks most critical security risks to web applications.
-> use .innerText instead of .innerHTML, avoid eval(), dynamic build of XML or JSON, keep secrets at Server, and also encrypt there.

Web Components - Standardised browser technologies to reuse HTML elements. Custom Elements for new HTML tags using JavaScript DOM API's, Shadow DOM for encapsulating styles and markups that reduces naming conflicts and CSS Specificity rules, HTML Templates for fragments of reusable HTML using <templates>. Ensures long term compatibility and interoperability in web ecosystems.

Type Checkers - Tools to analyse and prevent type-related runtime errors. Enforce type consistency by adding static typing to dynamically typed languages. eg - Typescript enables interfaces, generics, decorators for more robust software archtiecture.

Server-side rendering - Web pages generated on server and sent to client as fully rendered HTML. Improves load time and SEO for crawlers. Content heavy sites benefit, irrespecitve of server load.
eg - React and Next.js(SSR), React-router(CSR with nested routes, route parameters etc)
Next.js enables optimizations, dynamic HTML Streaming, CSS Support, React server components, middleware for authentication, data fetching etc.

GraphQL - Query language and server-side runtime for API's. Helps build complex applications with diverse client requirements.
Define types and their fields, and write function for each field to provide the data.
1. Relay is a data-fetching Javacript library working with GraphQL. Helps catching, pagination, batching requests wih a declarative approach for large scale projects. 

Progressive Web Apps - Use modern capabilities to combine web and native app features. Built using Web tech but have native app features such as offline functionality, push notifications, home screen installation. Discoverable through search engines, and use service workers for background processing and caching for faster load and offline access. Cost effective to develop and give app-like experience in browser.

Measure and Improve Performance -
1. PRPL Pattern: Architecture strategy to improve performance in mobile devices. Push, Render, Pre-Cache and Lazy-Load - push critical resources for initial route, render route quickly, pre-cache remaining routes/assets, and lazy-load non-critical resources.
2. RAIL Model(Google): User-centric performance model to improve responsiveness. Response(100ms), Animation(60 frames/s), Idle(deferred work) and Load(5 seconds for ineractive work).
3. Performance Metrics: Quantitative measures of web page performance. Load Time, First Contentful Paint(FCP), Time to interactive(TTI), First Input Delay(FID), Total Blocking Time(TBT) of main thread to become Interactive too.
4. Lighthouse: Open-source tool to audit performance, accessibility, SEO of web pages. Browser Extension and CL tool, which simulates load and interaction, check issues, and provide solutions to fix them.
5. Browser DevTools: Built-in features in modern web browsers to inspect, edit and debug in real-time. DOM Inspector, Console, Network panel, Performance profiler, Application Panel etc.

Browser APIs -
1. Web Storage API: Stores key-value pairs in web browser. LocalStorage, SessionStorage save data on client side and persist it across multiple browser sessions.
2. WebSockets: Allow full-duplex communication over single TCP connection. For high-speed low-latency communication without client having to send additional requests.
3. Server sent events: Web Server pushes data to client in real-time, where client listens events and take action such as chat systems, social media feeds. Client creates EventSource object that specifies URL of server-side script that sends events.
4. Service Workers: Web worker that is proxy between web page and network. Intercept network requests, access cache, make decisions on how to respond to request based on available resources. Written in JS and registered by web page. Provides push notifs, background synchronization etc.
5. Location API: Device location data using device GPS, wifi, sensors etc. navigator.geolocation object
6. Notifications API: System-level notifications to alert new messages or updates, even when web page isn't open. Notification constructor.
7. Device Orientation API: Access to device orientation and motion data for AR and motion controlled games. DeviceOrientationEvent object
8. Payments API: Checkout flows. Browser-based interface for collecting payment and shipping information. PaymentRequest Object for options, and then show() method to invoke Request UI.
9. Credentials API: Websites interact with browsers credential manager to store, retrieve and manage user credentials. Helps automatic sign-in and one-tap sign-up.

Static Site Generators - Tools to create HTML Websites from raw data and templates, producing pre-rendered pages at build time rather than at run time. Markup languages like Markdown for content, templating engines for layouts, and generate Static sites hosted on web servers or CDN's.
eg - Next.js