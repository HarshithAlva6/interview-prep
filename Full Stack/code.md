* **Static Webpages:** Simply using HTML and CSS
* **Interactivity:** Using JS and TypeScript
* **External Packages:** Node.js is JS runtime for server, while Node Package Manager for libraries on client/browser end. 
In order to dig the node modules to find location of package to add in HTML, JS module **Bundler(webpack)** will build system files for final output(script) which is browser compatible(no require/import statements)
**Babel/TypeScript** helps transpile code to browser compatible ones. Each time JS is changed, re-run the webpack.
**Task Runner - npm scripts** automates parts of build process
* **Collaborative Work:** **Git** is a free and open source distributed version control system (manage changes to software code). **Github** provides a collaborative environment.
* **FrontEnd Apps:** **React** and **Tailwind CSS**

* **CLI Apps:** Asynchronous event-driven Javascript runtime, hence no thread concurrency. Read/Write files, parse CLI/JSON/CSV, Make HTTP requests, use third-party API.
**PostgreSQL** is an open source relational database. Install server, and connect using *psql* in terminal and *pgAdmin* using Web.
psql -U postgres // SELECT current_database();
* **CRUD Apps:** Create, Read, Update, Delete todo app using Application Programming Interface built upon Representational State Transfer rules.
**JSON Web Token:** are standards for compact way of transmitting information between parties via JSON objects. Digitally signed for verification using secret/keys(HMAC/RSA).
Signed tokens verify integrity of claims, and if encrypted it can also hide the claims. Single Sign On uses JWT for small overhead and domain availability. Signature calculated using header("alg": "RSA", "typ": "JWT"), payload(claims) and secret using Base64URL Encode.
An Auth server creates JWT, signs it. Client sends same JWT in REST API request, which will verify signature. Then the claims can grant or deny Client's request.
**Redis(REmote DIctionary Server):** Open source in-memory data structure *store* used as database, cache, message broker, streaming engine. Built-in replication, LRU eviction, transactions, partitioning with Redis Clusters.
Redis Cloud create account -> database. 
>redis-cli -h 127.0.0.1 -p 6379
* **Complete App:** This is where the Full Stack section ends.


* **DevOps:** Starts with **Linux** with PATH environment variables telling Shell where to look from root(/). Flags ("man command" for manual). r(4): read, w(2): write, x(1): execute permissions for users, groups, owners
**Basic AWS Services:** -
1. **Route53:** AWS Domain Name System helps connect user requests to web application, redirect traffic, configure domain-related settings.
2. **SES:** Simple Email Service is cloud-based email service.
3. **EC2:** Elastic Compute Cloud is web service which provides compute capacity in the form of virtual servers/instances