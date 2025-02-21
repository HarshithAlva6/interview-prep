**System Design** - Define elements of a system, their interactions and relationships. A problem statement is broken down into individual components to design iteratively, and work together to achieve the goal of the system.
**How to approach?**
1. Understand the problem, users, needs, constraints, requirements.
2. Identify scope of the system(boundaries)
3. Research and analyse existing systems. Identify what worked and what didn't to update decisions.
4. Create a High Level Design - Start with functional and then non-functional components, their flowchart and architecture.
5. Refine the design - iterate until detailed design is built.
6. Document the design
7. Continuously monitor and improve the system
**Performance vs Scalability:** Service is scalable if performance increases when resources are added.
If scalability is issue, system would be fast for single user but slow under heavy load.
Caching if data doesn't change, no variety, and no loss.
Use Message queues(like in marshalls!) sent to Workers(Cashiers) for processing.
**Latency vs Throughput:** Latency is time taken to respond to request. Throughput is number of requests handled at some unit time (memory bandwidth). Aim for maximal throughput with acceptable latency.
**Availability vs Consistency:** Availability is ability of system to provide services even in presence of failures(uptime - percentage of time system runs).
Consistency ensures all clients see same data at same time. 
Partition Tolerance states system should continue to function when network partitions occur.
CAP Theorem states only 2/3 can be handled across write/read pair. 

**Consistency Patterns:**How data is stored and managed in distributed system.
1. Strong Consistency - Immediate propagation of updates to all locations, but system is less available, high latency. eg: Financial systems
2. Weak consistency - Subsequent reads may or may not reflect changes made/see recent write. High availability and low latency. eg: Gaming systems
3. Eventual Consistency - If update made, eventually visible to subsequent read operations. (Asynchronous) Data available in multiple locations, hence highly available, low latency. eg: Social Media. Updates found for users in same data center immediately, but takes time for propogation.

* **Availability Patterns:** Percentage of uptime. Cloud applications provide users with Service Level Agreement(SLA) stating how they maximize availability.
*Availability measured in number of 9s*. A service with 99.99% availability is described as having four 9s.
* Availability in Sequence - Decreases if both have availability < 100%
* Availability in Parallel - Increases. 
Total = 1 - (1-Availability(Foo)) * (1-Availability(Bar))
-> Passive Redundancy: Backup components take over in case of failures.
-> Active Redundancy: Active components work simultaneously, ready to replace in case of failure.
1. **Fail-Over** Function coninues in event of failure using backup component. Primary component monitored for failures.
1. Active-Passive - Send heartbeats between active and passive server on standby. If heartbeat interrupted, passive server takes over active's IP address and resumes service. Length of downtime determined by passive server if its on 'hot' standby or start up from 'cold' standby. ONLY active server handles traffic. (Master-slave failover)
2. Active-active - Here both manage traffic. Public-facing servers should share their IP's to DNS. Internal-facing servers share it to application logic.
(master-master failover)

2. **Replication** Multiple copies of same data stored in different locations.
1. Master-Master - Multiple Servers configured as masters, hence high availability. But conflicts arise if they update same data at same time, hence conflict resolution mechanism needed.
2. Master-Slave - One server is Master for write operations, and slave servers handle Read. When Master fails, one of the slaves is promoted. 

**Background Jobs** Tasks running in background, independent of main flow. Initiated by systems such as batch jobs, workflows, triggers(event or schedule driven).
Maintaenance tasks such as cleanups or backups.
Data Transformation tasks, sending email notifs, or long-running ML Computations.
1. Event Driven - UI places message in queue. This has data about the action to take place. This data is input to background job in asynchronous manner.
2. Schedule Driven - Timer based.   Could run on local application, or different one sending API requests to invoke the task.
-> Returning Results: Background tasks are fire and forget operations(no impact on actual UI or calling task)

**Domain Naming System** Translate Domain name to IP Address and vice versa. ISP provides info about DNS Server to contact for lookup. 
*Time To Live(TTL)* determines caching time of DNS results.
Eg: Cloudflare, Route53
**Content Delivery Networks** Globally distributed network of proxy servers, serving content at locations closest to user. Mostly static files, but dynamic content too via *Amazon's Cloudfront*. Servers needn't handle requests if CDN can fulfill. Amount of data downloaded from your server is charge of CDN's.
Need to rewrite API's to CDN.
1. Pull CDN - First user request when its published on local server and awaiting to be uploaded in CDN, this is when CDN pulls. This is slow but immediate.
2. Push CDN - When content loaded in CDN Server, and can be accessed anytime later.
-> Pull CDN seamlessly stores contents as and when requested, and tends to be fast on low traffic sites.
Websites with large download files prefer push CDN, compared to high-traffic small-download sites which prefer pull CDN.

**Load Balancers** Distribute client requests to computing resources such as application servers and databases. Implemented using Hardware or Software(HAProxy) and can increase complexity if not configured right. Benefits include -
1. Decrypting incoming requests and encrypt server responses(SSL Termination)
2. Session Persistence by issuing cookies, hence maintain client request to same instance. Or cache Persistence using **Redis**. Codebase from servers can persist on all the servers using **Amazon Machine Image**.
Sharding, Denormalization of MySQL, master-slave replication -> Upgrade to NoSQL which handles joins on code -> In-memory cache using Redis. Buffering layer between client and data storage. Two patterns -
1. Cached Database Queries - Query is hashed as key, results are values. Hard to delete a cached result of complex query, or if resut cell changes.
2. Cached Objects - Like how code handles classes as objects, see the data too accordingly. Easier to get rid of, and handle asynchronously.
-> RabbitMQ helps to handle async processing.

**LB vs Reverse Proxy** LB when multiple servers. RP used even with just one web server, but more complex.
RP is a device acting on behalf of other devices, forming a service. Forwards client requests to web servers, and response or resources return to that RP, as if they sent the request. Websites "public face".
Additional level of abstraction, can direct requests based on parameters such as user device, location, network conditions etc. Help prevent Distributed Denial-Of-Service attcks on backend servers.
Provide firewalls, content inspection, forwarding service.
1. **NGINX** Master process handles config and port binding, four worker processes and couple of cache helper processes (cache loader and cache manager)

**LB Algorithms**
**Dynamic LB Algorithms -**
1. Least Connection - Check server with least connections, if all require equal processing power.
2. Weighted least connection - Admins have ability to assign weights to servers, accordingly serve request.
3. Weighted response time - Average response time, plus number of connections open.
4. Resource Based - If server has enough resources at that time. *Agents* running on the server measures servers available CPU and memory
**Static LB Algorithms -**
1. Round Robin - In Rotation using DNS, from an authoritative nameserver.
2. Weighted Round Robin - Admin assigns weights to servers, configured with DNS records.
3. IP Hash - Combine incoming source and destination IP addresses, convert into hash. Accordingly assign to servers.
**Layer 7 LB** Look at application layer, such as header contents, messages, cookies. They terminate network traffic, reads message, lakes a LB Decision, then OPENS a connection to selected server.
**Layer 4 LB** Look at Transport layer, such as source, destination IP Addresses, ports. Forward network packets by performing Network Address Translation(NAT).
**Horizontal Scaling** Commodity hardware scaling more cost effective. But servers need to be stateless, and store sessions in database or cache.

* **Application Layer** Adding API results in more App servers, seperate from web servers. Requests from client go to LB, web server, platform/application server for processing, and finally Database.
**MicroServices** Independent small services. Its called Service Oriented Architecture.
**Service Discovery** *Zookeeper* helps find the services via their name, addresses, ports. 
Health checks done using HTTP endpoint by verifying service integrity.

* **Databases** Based on Performance, Scalability, Data Modelling, Data Integrity, Support and Maintenance.
1. **NoSQL -** 
Key Value Store(O(1)) lexicographic order, stores metadata too. In-memory cache, complexity shifted to app layer, and handles simple data models.
Document Store (XML, JSON) provides API's/query language. Organized by collections, tags, metadata or directories.
Wide Column Store (name/value pair in columns). eg: Bigtable, HBase, Cassandra maintain keys in lexographical order.
Graph Database has nodes as records, help represent complex relationships.

2. **RDBMS -**
1. Replication - Process of copying data to increase availability, scalability. Master-slave and Master-master
2. Sharding - Distribute data across databases, each handle subset of data such as users(rows). Less replication, more cache hits, smaller Index size. Can write in parallel with increased throughput, since no Master.
3. Federation - Split monolithic database by function, resulting in less read, write traffic to each database. Increased cache hits, more data, parallel writes.
4. Denormalization - Redundant copies written in multiple tables, avoids joins. If data gets distributed by above two methods, joins get complex and this could circumvent it.
5. SQL Tuning - Diagnose/repair SQL statements which fail performance standards. (User response time and throughput) Use Benchmarking and Profiling.

**SQL vs NoSQL** SQL provide ACID transactions and has fixed schame.
NoSQL has flexible schema, hence high scalability and performance.
**Caching** Store frequently accessed data temporarily.
*Caching Types -*
1. In-memory/Application Caching - Store in RAM for high-speed access, but volatile.
2. Distributed CDN Caching - Store across servers/nodes for high availability, performance and scalability, but hard for consistency.
3. Client-side caching - Store on web browser, i.e., client's device. Best if data is stale. Application-level caching is caching on the device, not browser
4. Web Server Caching - Reverse Proxies such as Varnish and web servers can handle.
5. Database Caching - Quick access(Copy in cache), Faster Retrieval, Saving Time, Different Types(bookmark results, copy or snapshots)
*Caching Strategies -* 
1. Refresh-ahead - Cache automatically refreshes recently accessed cache entry prior to its expiration. Reduced latency.
2. Write Behind - Add/update cache entry, and asynchronously write cache entry to the database.
3. Write Through - Cache used as main data store by application. Cache in turn is responsible to read/write to database synchronously. 
4. Cache Aside - App reads/writes from storage, and cache doesn't interact with storage. App looks for entry in cache, and if not found it pulls from database and adds to cache. Lazy loading by Memcached.

* **Asynchronism**: Reduce expensive operation request time, and also handle work in advance.
1. Back Pressure - Limit queue size, high throughput rate and response for jobs in queue. Once filled, client gets HTTP 503 Status code.
2. Task Queues - *Celery* helps process vast amounts of tasks, related data, run and deliver results in real-time via scheduling in background. Stays in queue until processed.
eg: Ticket system in kitchen using Paper
3. Message Queues - When app sends job to queue, it notifies user of job status. Worker picks up these jobs, process it and signal when complete. If notification missed, processing lost.
eg: Ticket system in kitchen using loudspeaker - Redis, RabbitMQ, Amazon SQS, Kafka

* **Idempotent Operations** Operations which even if applied multiple times, has same result of the initial run.

* **Communication** Networking protocols help systems communicate.
1. HTTP - Encode and transport data between client and server in request/response protocol. Application layer protocol relying on lower-level protocols such as TCP/UDP.
2. TCP - Connection-oriented protocol over IP Network. Established using handshake. Sent in an order using sequence numbers and checksum fields for each packet. Web servers keep large number of TCP connections, hence large memory usage. BUT ensure highly reliable if less time critical.
3. UDP - Connectionless, Datagrams reach without an order, but more efficient since they broadcast to devices on subnet. Less reliable but wokrs best for VoIP, video chat, streaming etc.

1. RPC(Remote procedural call) - Client causes procedures to execute on remote server address space. Coded as if it were a local call. Some frameworks are **Protobuf, Thrift**. 
Request response protocol, client calls procedure, where parameters pushed onto stack. Procedure ID and arguments are packed into request message. OS Sends this from client to server, and server sends the incoming packets to server stub procedure. Here it is unmarshalled, id checked with the server procedure. BEST for microservices.
2.  gRPC - Open source framework to build RPC APIs. Supports various programming languages unlike RPC. Messages are serialized/deserialized using in-memory schema into binary messages.
3. REST
4. GraphQL

* **Performance Antipatterns** Common suboptimal practices which lead to poor performance. A common Response to a recurring problem which is counter producive.
1. N+1 Queries: If system takes multiple queries to retrive related data instead of a single query.
2. Chatty Interfaces: If system makes many small frequent requests to API instead of fewer larger requests.
3. Unbounded data: If system returns more data than necessary, leading to increased resource usage.
4. Inefficient algortihms: If not suited, leading to reduced performance too.
5. Busy database: Don't offload processing onto data store. Could lead to degradation, deadlocks, inconsistenceies. Prefer scaling out, optimiziing schema, caching, Indexing.
6. No Caching - Excessive calls, repeated object construction.
7. Monolithic persistence - No single database, could cause bottleneck. Ensure Microservices, Sharding, NoSQL databases.
7. Improper Instantiation - Unnecessary object instances created. Instead pass as a dependency injection on constructors.
8. Busy Frontend - Resource intensive tasks on background can starve foreground tasks. This decreases response times to unacceptable levels.
9. Noisy Neighbor - When components utilize disproportionate amount of shared resources, leading to slow I/O and increased latency.
10. Synchronous I/O - This blocks calling thread once I/O completes, wastiing processing resources. This is when app requires response, uses libraries that have synchronous methods only.
11. Retry Storm -  Large number of entries triggered at once. Do exponential backoff, circuit breaking, monitoring and alertings.
12. Extraneous Fetching - Retrieve more data than needed. More resource utilized, more traffic and performance degradation.

* **Monitoring** Distributed applications running on cloud comprise many moving parts. In Prod, we should be able to track users, resource utilization, health and performance of system, maintain SLA, protect privacy, track issues.
1. Health Monitoring - Snapshot of current health to verify functionality to handle requests.(Traffic signals)
2. Availability - Tracks availability to generate statistics about uptime. If there's built in redundancy solutions, failovers must be analysed.
3. Performance - Stress from volume of users increases datasets size. Failure preceded by performance decrease. Look for key performance indicators such as response rates, concurrent user requests, network traffic, average processing time.
4. Security - More complex the mechanism, the more sensitive the data. Record all sign-in attempts, operations performed by authenticated users, and when user ends a session and signs out.
5. Usage - How features and components used. Can spread load during high traffic by replication, or decide which features are candidates for retirement.
Based on number of transactions and volume of customers, determine capacity - which helps detect user satisfaction.
Needed for billing, and enforce quotas to limit or throttle processing after a threshold.
6. Instrumentation - Capture data, helps assess performance, diagnose problems and decisions without signing to remote prod server to trace and debug manually. (Categorized Logs or Metrics - measure of resource)
7. Visualization and Alerts - Present data to immediately identify trends or problems.
