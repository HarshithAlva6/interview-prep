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
