**API-** Protocols that use functions from other software applications to communicate. Abstract the complexity of applications by defining methods and data formats to perform tasks such as sending/retrieving data.
Client <-Response - Request-> API <-> Server.
A request has endpoint(URL), Method, Parameters(instructions), Headers(key-value metadata), body(for POST)
A response has status code, headers, body(for GET)
**HTTP:** (Tim-Berners Lee) Hypertext Transfer Protocol is a TCP/IP-based application layer communication protocol used to transmit HTML webpages/JSON from web API. Explains how requests/responses should be constructed. We use TCP port 80, but HTTPS uses port 443.

1. HTTP/0.9 - One line protocol
GET /index.html
2. HTTP/1.0 - Building extensibility. Response had status code.
GET /my-page.html HTTP/1.0
3. HTTP/1.1 - The standardized protocol with connection reuse, pipelining to reduce latency, accept chunked/cached responses.
4. HTTP/2 - Protocol for greater performance. Binary rather than text protocol. Multiplexed, hence parallel requests can be handled. Compresses headers to reduce overhead.

**HTTP Request methods:** Verbs such as GET, HEAD(no body), POST, PUT, DELETE, PATCH, OPTIONS (communication options), TRACE(message loop-back test)
**HTTP Status codes:** 200(OK), 201(Created - for POST/PUT), 301(Moved Permanently), 400(Bad Request), 401(Unauthorized), 403(Forbidden - Unlike 401, here client is authenticated), 404(Not Found), 500(Internal Server Error), 502(Bad Gateway)
**HTTP Headers:** Accept(Media Types/MIME accepted), User-Agent(Web browser), Authorization(JWT), Content-Type(Media type), Cookie, Server(Web Server for response), Content-Length.
*Cookies:* Sent by server to client, stored in browser, enables stateful HTTP sessions, such as authentication to store session tokens(users can stay logged in across multiple sessions or different web pages)
API vs HTTP Cookies 
**CORS:** Mechanism using HTTP Headers to tell browsers to give a web application in one origin, access to resources from a different origin without security compromise.
**Caching:** Store copies of responses to HTTP requests to speed up future requests. Governed by headers, which helps reduce server load, latency and increase speed of an API.

**URL, Query Parameters and Path variables:** URL is the basis, query helps filter results(/balls?color=yellow), path acts as placeholders for variable data taken as input into URL(/{ballId}).
**Content Negotiation:** Client-server accept common data representation. This is when server can choose amongst variants(representations) of the response.
**Understanding TCP/IP:** Communication standard that helps connect hosts on Internet, enabling delivery of stream of bytes from one program on one computer to another computer.
FIRST, estabish connection that remains LIVE. Data broken down into PACKETS. Peer-to-peer sharing methods such as FTP, SSH(Secure Shell). Alternative to TCP is User DataGram Protocol(UDP) whic is better for DNS, VoIP(Voice over Internet Protocol)
To send data across the Internet, we use IP. It obtains and defines the IP address that identifies the devices
**Domain Naming System** interprets human-friendly domain hostnames into IP addresses that APIs need for communication. 
Once registered, creates DNS Record with Type, host, value, which maps to the IPv4 address

* **API Styles -**
1. Resource-style API - Expose reswources to consumers such that they can interact with them. **Representational state transfer (REST)** is an architectural pattern for the resource style, with HTTP protocols and JSON represntation.
2. Hypermedia style API - Adds a key component to the resource style to address resource-linking concerns between webpages via links.(dynamic resource routing)
3. Query Style API: Single Entry point for large set of resources - managed in a structured form by API provider. Hence can be queries to fetch only necessary results. **GraphQL** returns JSON. Unlike REST API's which leverage HTTP Caching, here its complicate, and lack of rate limiting. Use API Gateway to handle both issues
4. Tunnel Style API - Collection of functions/procedures invoked remotely, all exposed. Minimal effort to create. Remote Procedure Call(RPC) is a request-response protocol where client sends request to remote server. **gRPC** for distributed systems.
5. Event-based API - Provider delivers events to consumers, which indicate change of state of any specific record. Message Broker decouples the two, where consumers should subscribe to event types. **Apache Kafka** is considered.

**REST Principles:** Client-Server, stateless(no session state to authenticate - self authenticated client), cacheable resources, Uniform interface, layered system. Resources identified using **Uniform Resource Identifier(URI)** similar to **Uniform Resource Locator(URL)**. Related resources grouped in logical manner, eases use and maintainability. Modern CMS Systems allow URI Customization. Its Principles are -
Represent Data Object,  Permanent, Human-friendly, shortlink flexible, Consistent structure, Hackable, Keywords only helps SEO, no evidence of underlying technology, no WWW, lowercase, should be URI friendly
**API Versioning:** Process of managing and tracking changes to an API, communicating those changes to the API's consumers. "Breaking issues' cause backward compatibility issue. Some changes such as Renaming endpoint, Turning optional into required parameters, modify data format, or property characteristics.
Types - 
URL, Query Parameter, Header, Consumer-based(Semantic).
**Handling CRUD Operations in API Design**
**Pagination:** Client can fetch large data incrementally. Limit-offset, cursor-based, time-based.
**Rate Limiting:** Number of API Calls within a timeframe for resource allocation.
**Idempotency:** Multiple identical requests equal to single request on server state. POST and PUT usually non-idempotent. (Essential in transcations to not duplicate money request)
**HATEOAS:**Hypertext As The Engine Of Application State, provides data and interaction information. This constraint uses hypertext in API response. (Hypermedia style API)
**Error Handling Practices:** 
1. Clear and consistent structure for idempotent responses.
2. Descriptive Error Messages
3. Don't leak sensitive data
4. Document Common errors
5. Implement logging
-> RFC 7807 Standard is Problem Details for HTTP API's. No confusing error message, just a structured JSON Error Response.

**Types of API's -**
1. *RESTful API* - Works on REST principles, utilize HTTP methods.
2. *JSON API* - Utilize JSON which reduces redundant data, quick parsing.
3. *SOAP API* - Simple Object Access Protocol permits programs on different OS to communicate using HTTP and its XML. Highly extensible, versatile, reliable. Useful for business focused, high transaction applications.
SOAP has official standards with HTTP and XML, unlike REST using URL and HTTP. SOAP uses @WebService and XML to create the payload, and language flexible.
4. *GraphQL API* - Have type system that ensures what data it needs. Fewer round trips to fetch more resources in a single request.
5. *gRPC* - Modern alternative to REST APIs. Binary protocol using HTTP/2 as transport layer for serialization. Communication between two different laanguages under SAME application, by calling functions DIRECTLY on the other server. Uses Protobuf.

* **Authentication Methods in API**
 Process to verify the identity of a user who is making an API request.
 1. **HTTP Basic authentication -** 
 Request resource -> 
 <- Request username/password
 send username/password -> (in Authorization header, Base64 encoded, seperated by colon under HTTPS protocol)
 <- Returns requested resource, else 401 
 2. **API Key Authentication -**
 Client gets API Key from API provider. When client makes Request via API Server, add this API Key under HTTPS.
 3. **JWT Authentication -** Stateless mechanism
 When client logs in, API Server creates digitally signed and encrypted JWT with user's identity.
 Client sends auth request with JWT in header, and even on every subsequent request. This way the user data doesn't have to be stored on server's side, which in turn increases scalability.
 Toeksn have Header(Toekn type and signing algorithm), Payload(Token issuer, expiration), Signature
 Pros: Small size, ease, control.
 Cons: Single Key, Complex, limitations to manage clients
 4. **OAuth Authentication -** Token-based
 Third-party is delegated authorization and access to service that hosts user/*client* account without credentials. This party then sends this grant for Access token from *Authorization server*, and in return this token is used to fetch Resource from *Resource Server*. 
 OAuth 2.0 is gold standard
 5. **Session Based Authentication -** Server creates session with session identifier after client logs in. This ID stored in client side Cookie. Server validates this ID with the one in their Session file before processing request, and destroy session once user logs out.
 Cons: scalability, Multiple domain requests, lack of security(Cross-Site Request Forgery)

 * **Authorization Methods in API Design:** Ability to access digital resource.
 1. Role-based access control(RBAC) - User access granted based on roles within organization. Administrators can manage easily. Streamlined plug-and-play setup, quick to change and is compliant.
 2. Policy-based Access Control(PBAC) - User roles, associated permissions, and additional attributes used to determine access. Grants admins more flexibility and spped, adaptability(time and location bound), observable(Policies are human readable, can view identities and resource relationship)
 3. Attribute-based Access Control(ABAC) - Use characteristics to dynamically determine user access priviledges. Focus on attributes that influence the policies. Won't have to create new roles, just add attributes to new users. 
 User(type, role, dept), Environment(Time/date/location/device), Resource(File name, sensitivity)

 **API Key and Management:** Ensure API storage, RBAC, Rate Limiting to prevent DoS attack.
 Along with keys, Secrets management includes passwords, Encryption keys, SSH keys, Authorization tokens, Private Certificates.
 **API Documentation Tools:**Needed to explain technical developers and non-technical stakeholders. Swagger, DapperBox and ReDoc.
 1. Swagger/Open API - Design(Editor), build(codegen) and document (UI) RESTful Web Services. Use Open API Specification to work across various programming languages.
 2. Readme.com - Doesn't just present information, but enhances reader's understanding by making it interactive.
 3. Stoplight - Also uses OpenAPI specification, allowing users to design APIs visually. Auto-generate, perform API mock testing, easy-to-use, scalable.
 4. Postman - Most popular. Streamlines collaboration across teams. Endpoints can be organized into collections for well structured API design process.

 * **API Security:** Safeguard data, prevent unauthorized access, protect system hosting API.
 **Best API Design Practices -**
 Accept and respond with JSON. Use nouns instead of verbs in endpoint paths, logical nesting, handle errors gracefully with standare return error codes, allow filtering, sorting, pagination, add SSL certificate, Cache data, version API
 **API Design vulnerabilities:** 
 Broken Object-level Authorization check, Broken user authentication, Injection Attacks(Malicious code into API Request), Excessive Data exposure in responses, lack of rate limiting, Insecure Direct Object Reference(Use indirect references instead)
-> Use Input Validation, strong authentication and authorization, throttling(slow down processing of requests once limit reached), API Gateway(abstraction layer), API Vulnerability scanning tools.

* **API Performance:** Efficiency of executing requests.
1. Cache data
2. Limit Payloads via Pagination, GraphQL
3. Simplify Database queries. Use AI to monitor network traffic and API calls. Event-driven architecture avoids this (API Polling).
4. Optimize connectivity and reduce packet loss.
5. Rate Limit to avoid abuse
6. Implement Pagination
7. Use asynchronous Logging
8. Use PATCH instead of PUT(smaller payloads)
9. Compress Payloads(gZip)
10. Use a connection Pool

**Performance Metrics:** Response time, Latency, Failed request rate, Throughput, Availability.
Do logging, alertingend-to-end transaction monitoring
**Caching strategies:**
Helps improve response times, scalability, reduce network traffic, improve readability, cost savings, better use of resources.
1. Client-side caching: Static content such as images, videos, mainly on mobile devices. 
HTTP Cache headers, Local Storage, Service Workers(website background scripts), Cache API(web API)
2. Server-side caching: Repeated requests for changing/calculated data. 
Database caching, In-memory caching(Server RAM), File system Caching, Reverse Proxy caching(intermdeiary server), CDN Caching.
**Load Balancing:** Component that distributes network traffic across group of backend/API Servers, and HTTPS offloading. Not to confuse with **API Gateways** which help in traffic control(caching and rate limiting), authenticate and authorize, metrics and logging. Its more specific and hence is added after Load Balancer.
**Rate Limiting and Throttling:** RL happens at client level. Throttling can also block clients that exceed allowed request rate, request queuing, concurrent request limiting, bandwidth throttling, hence server level.
**Profiling and Monitoring:** Profiling is analysing the behavior of API to understand performance metrics and optimization, and monitoring is ongoing process of checking status of API.
Profiling - Event-based, Statistical, Memory
**Performance Testing:**Evaluating API performance under varying workloads. 
Load Testing(max operating capacity), Endurance Testing(conintuous usage), Stress Testing(Breaking point), Spike Testing(Sudden user load increase), Volume Testing(Simultaneoud data processed) OR Passive API Monitoring.
**Error Handling/Retries** Error message or status codes to exceptions. Retries ensure max success amidst transient failures. *Back-off* concept ensures delay between retries that increase over requests.

**API Integration Patterns:**
Understand Error Codes, Granularity(Design main use cases using common terms, keeping developers in mind), URLs with nouns, Authentication(API keys, OAuth, Webhooks which is push-based - URL recieves updates when it occurs)
1. Synchronous vs Asynchronous APIs - 
Request, processing, response.
Request, acknowledgement, Processing, notification(webhook/callback)
2. Event Driven Architecture - Production, interpretation and consumption of events. Asynchronous, hence real-time data delivery and reliability.
Event Producers -> Event Ingestion -> Event Consumers
-> **Pub/Sub Model** Event Published, sent to all subscribers via topics which send it in message queues. Can't be replayed, and new subscribers can't see event.
-> **Event Streaming** has events on log. Ordered within a partition. Clients can read from any part of the stream, move across, or replay.
-> Event Stream Processing using **Apache Kafka** which is a pipeline with events, fed to stream processors to process the data.
3. API Gateways - Authenticate, rate limit, billing system, adopt microservices architecture, caching.
4. Microservices Architecture - Each runs a unique business goal/responsibility, helps scalable deployment of large complex applications. Containers help in handling services without the dependencies between them(handled via **Kubernetes** later)
5. Webhooks - When event takes place in source application, an HTTP request which might contain data relating to the event is triggered. This HTTP request is sent to the destination application's endpoint (webhook URL).
6. WebSockets - Two way real-time communication by keeping a socket open on both the client and the server for the duration of the conversation.
7. Batch Processing - Multiple API Requests without opening multiple connections. *Bulk import* is single request for large dataset import, and *batch import* deals with breakdown of large datasets into batches
8. Messaging Queues - Lightweight buffer that help scalabiity, fault tolerance, system resiliency via high data processing in asynchronous manner. Processed once and deleted. **Rabbit MQ and Kafka**

* **API Testing**: Not UI, but business logic.
1. Unit Testing - Dev stage, isolate each component and check operation. Use **Chai/Mocha**
2. Integration Testing - Units combined and tested as a group. Help expose faults in interaction between integrated units. Boundary values, backward compatibility, error handling. Use **requests-mock**
3. Functional Testing - Validate endpoints and key-value pairs of API if it's functioning. Gives insights if API meets requirements, and if ready for integration.
4. LOad Testing - Test capacity of API in terms of volume of requests, and behaviour when threshold is reached/overloaded. This helps improve resilience.