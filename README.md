# System Design Interview Checklist: 

Usually, the System Design interviews are lengthy and cover a lot of complex components. This makes it very easy to get lost in small things and miss out on the big picture. Therefore, it becomes very important to structure your interview in a way such that you can easily convey the whole picture without wasting time on anything which does not add value.

<img src="https://github.com/rajeevranjancom/System_Design/blob/main/Pic/vbnm.png" style="max-width: 100%;" alt="Welcome images" />


# Drive the interview

Make sure you are the one driving the interview and not your interviewer. This does not mean that you do not let them speak, but rather, you should be the one doing most of the talking, proactively calling out issues in your design before the interviewer points it out, handle the edge cases that the interviewer might poke you on etc.

# FRs and NFRs:

Clearly call out the Functional and Non-Functional requirements. The intent is that the requirements should be big enough that makes the problem challenging and also finite enough that you can build a system that fulfills those requirements within the stipulated time. From the Non Functional side, try to make a system that works at a very large scale. What’s the fun in designing a system which works at a low scale?
Before finalizing the FRs and the NFRs, get them reviewed with your interviewer to make sure they do not want to add/ remove something. At times, interviewers do have some particular use cases in mind that they want to go over.

# Capacity Estimation:

Check with your interviewer if they want to get into this. A lot of people prefer to skip the calculations and focus more on the design, assuming a large enough approximate number for the number of cores required or the amount of disk required etc.

# Plan:

Based on the FRs and NFRs, come up with these things:
User Interaction Points.
Latency/ Availability/ Consistency requirements at each of the user interaction points.
A quick analysis estimating if it’s a read-heavy interaction or a write-heavy interaction.
Based on the above three, come up with what all services you’ll need and what kind of databases you can use to store the data that each of these services owns.

# HLD:

Come up with a high level component diagram, that covers the following:
What all services are present? Make sure you divide the flow into multiple functional components and see if a microservices based approach makes sense or not. Usually, using a microservices based approach is a good idea in SD interviews.
How do the services interact with each other and what kind of protocols are used for inter service communication like Async/ Sync — Rest, RPC etc?
How would the users interact with the whole system and what all services are user facing. Do you need a Cache to reduce latencies?
Which service uses what Database and why? You can refer to this video that can help you choose the right database based on your use case
See if you need caching anywhere and if you do, then what shall be the eviction policy, do you need an expiry for the keys, should it be a write through cache etc?
Basis all this analysis, draw out a High Level Diagram of your whole system.

# Must Haves:

Some key things your high level diagram should have are:
Load Balancers
Services
Databases and Caches
User interaction points
Any other tools like a Message Queue, CDN, etc.

# Walkthrough the design
Once you have the whole diagram ready, go over the whole design, one use case at a time and explain your design to your interviewer at a very high level. Talk about why you have chosen a particular database here and why you have used a particular mode of communication like Sync/ Async etc. You can also get into an RPC vs HTTP kind of a conversation if you made a particular design choice. You should go over what kind of data replication strategy is being used in your databases, for example, would you use a Master-Slave or a Multi Master setup etc.

# CAUTION: Do not go into the details like APIs, DB Schema etc right away unless the interviewer asks for it. Most people get lost in designing the APIs for just one system at this point and run out of time later on.
Brownie Points: Most interviews do not have FRs and NFRs around analytics, but if your design covers that or leaves good enough scope for analytics, that elevates your solution a lot. 

# Implementation:

Once you explain the whole flow to your interviewer, ask them which component they want to discuss in detail. Usually, people do not want to go over the entire system in detail. Let them decide which is that one component that they want to dig into and then you can go over the implementation details of that particular system.

# Things you should cover here are:

APIs — Call out the APIs that this system exposes. Make sure you are using the best practices here. For example instead of a GET API with URL like GET /user/getUserbyUserId, it’s better to use: GET /user/{id}
API Protocols — You can cover what protocols are you exposing the APIs on. Most people choose REST APIs, but you can decide to use something more efficient like Thrift, Protobuf etc based on your use cases.
Events — You can call out which events this particular service listens to, who produces that event, what payload comes in, what processing happens on that event etc.

# DB Schema: Go over the DB Schema here. You can also get into SQL vs NoSQL debate or why have you chosen a particular database, if you did not go over the same earlier while talking about the high level design.
If it’s a SQL, do talk about what indices you’ll have and how are you optimising your queries. In case of NoSQL, make sure you go over the consistency guarantees that the DB provides, can it cause any issues and the kind of queries you’ll run on that DB. Clearly call out the keys for key-value stores or the partition keys for a columnar store etc.

# Handle Murphy’s law:

This is something that most people skip but this is one of the most important things that you must cover which talks about how resilient your system is. In the real world, things break, and when they do, you need to make sure you are in full control of your system.
Talk about how you monitor the system. What kind of alerting mechanism do you have in place? What are your KPIs (Key Performance Indicators) and how do you track them? What happens when things break, when your service crashes, your DB’s master node goes down or even when one of your datacentres goes down?

Well this was for System Design, if you want to look at how was I able to crack companies like Google, Facebook, Amazon, etc, have a look at my Overall preparation strategy at:
Hope this helps!

## Table:

|  #  |      Title      | Tag  | 
|-----|---------------- | ---- |
|  1  | [Airbnb](https://github.com/rajeevranjancom/System_Design/blob/main/Airbnb.png) | Airbnb |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Airbnb.png" style="max-width: 100%;" alt="Welcome images" />

|  2  | [Amazon](https://github.com/rajeevranjancom/System_Design/blob/main/Amazon%20System%20Design.png) | Amazon |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Amazon%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

|  3  | [Facebook](https://github.com/rajeevranjancom/System_Design/blob/main/Facebook%20System%20Design.png) | Facebook |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Facebook%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

|  4  | [Google Maps](https://github.com/rajeevranjancom/System_Design/blob/main/Google%20Maps%20Design.png) | Google Maps |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Google%20Maps%20Design.png" style="max-width: 100%;" alt="Welcome images" />

|  5  | [Hotel Booking](https://github.com/rajeevranjancom/System_Design/blob/main/Hotel%20Booking%20System.png) | Hotel Booking |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Hotel%20Booking%20System.png" style="max-width: 100%;" alt="Welcome images" />

|  6  | [Notification Service](https://github.com/rajeevranjancom/System_Design/blob/main/Notification%20Service%20design.png) | Notification Service |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Notification%20Service%20design.png" style="max-width: 100%;" alt="Welcome images" />

|  7  | [Twitter](https://github.com/rajeevranjancom/System_Design/blob/main/Twitter%20System%20Design.png) | Twitter |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Twitter%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

|  8  | [Uber System](https://github.com/rajeevranjancom/System_Design/blob/main/Uber%20System%20Design.png) | Uber System |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Uber%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

|  9  | [Video Streaming](https://github.com/rajeevranjancom/System_Design/blob/main/Video%20Streaming%20Platform.png) | Video Streaming |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Video%20Streaming%20Platform.png" style="max-width: 100%;" alt="Welcome images" />

|  10  | [Whatsapp](https://github.com/rajeevranjancom/System_Design/blob/main/Whatsapp%20System%20design.png) | Whatsapp |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Whatsapp%20System%20design.png" style="max-width: 100%;" alt="Welcome images" />

|  11  | [Zoom](https://github.com/rajeevranjancom/System_Design/blob/main/Zoom%20System%20Design.png) | Zoom |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Zoom%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

# System Design Cheatsheet

> Picking the right architecture = Picking the right battles + Managing trade-offs

## Basic Steps

1) **Clarify and agree on the scope of the system**
* **User cases** (description of sequences of events that, taken together, lead to a system doing something useful)
	* Who is going to use it?
	* How are they going to use it?
* **Constraints** 
	* Mainly identify **traffic and data handling** constraints at scale.
	* Scale of the system such as requests per second, requests types, data written per second, data read per second)
	* Special system requirements such as multi-threading, read or write oriented.
	
2) **High level architecture design (Abstract design)**
* Sketch the important components and connections between them, but don't go into some details.
	* Application service layer (serves the requests)
	* List different services required.
   	* Data Storage layer
   	* eg. Usually a scalable system includes webserver (load balancer), service (service partition), database (master/slave database cluster) and caching systems.

3) **Component Design**
* Component + specific **APIs** required for each of them.
* **Object oriented design** for functionalities.
	* Map features to modules: One scenario for one module.
	* Consider the relationships among modules: 
		* Certain functions must have unique instance (Singletons)
		* Core object can be made up of many other objects (composition).
		* One object is another object (inheritance)
* **Database schema design.**

4) **Understanding Bottlenecks**
* Perhaps your system needs a load balancer and many machines behind it to handle the user requests. * Or maybe the data is so huge that you need to distribute your database on multiple machines. What are some of the downsides that occur from doing that? 
* Is the database too slow and does it need some in-memory caching?	

5) **Scaling** your abstract design
* **Vertical scaling**
	* You scale by adding more power (CPU, RAM) to your existing machine.
* **Horizontal scaling**
	* You scale by adding more machines into your pool of resources. 
* **Caching**
	* Load balancing helps you scale horizontally across an ever-increasing number of servers, but caching will enable you to make vastly better use of the resources you already have, as well as making otherwise unattainable product requirements feasible. 
	* **Application caching** requires explicit integration in the application code itself. Usually it will check if a value is in the cache; if not, retrieve the value from the database.
	* **Database caching** tends to be "free". When you flip your database on, you're going to get some level of default configuration which will provide some degree of caching and performance. Those initial settings will be optimized for a generic usecase, and by tweaking them to your system's access patterns you can generally squeeze a great deal of performance improvement.
	* **In-memory caches** are most potent in terms of raw performance. This is because they store their entire set of data in memory and accesses to RAM are orders of magnitude faster than those to disk. eg. Memcached or Redis.
	* eg. Precalculating results (e.g. the number of visits from each referring domain for the previous day), 
	* eg. Pre-generating expensive indexes (e.g. suggested stories based on a user's click history)
	* eg. Storing copies of frequently accessed data in a faster backend (e.g. Memcache instead of PostgreSQL.
* **Load balancing**
	* Public servers of a scalable web service are hidden behind a load balancer.  This load balancer evenly distributes load (requests from your users) onto your group/cluster of  application servers.
	* Types: Smart client (hard to get it perfect), Hardware load balancers ($$$ but reliable), Software load balancers (hybrid - works for most systems)

<p align="center">
  <img src="http://lethain.com/static/blog/intro_arch/load_balance.png" alt="Load Balancing"/>
</p>

* **Database replication**
	* Database replication is the frequent electronic copying data from a database in one computer or server to a database in another so that all users share the same level of information. The result is a distributed database in which users can access data relevant to their tasks without interfering with the work of others. The implementation of database replication for the purpose of eliminating data ambiguity or inconsistency among users is known as normalization.
* **Database partitioning**
	* Partitioning of relational data usually refers to decomposing your tables either row-wise (horizontally) or column-wise (vertically).
* **Map-Reduce**
	* For sufficiently small systems you can often get away with adhoc queries on a SQL database, but that approach may not scale up trivially once the quantity of data stored or write-load requires sharding your database, and will usually require dedicated slaves for the purpose of performing these queries (at which point, maybe you'd rather use a system designed for analyzing large quantities of data, rather than fighting your database). 
	* Adding a map-reduce layer makes it possible to perform data and/or processing intensive operations in a reasonable amount of time. You might use it for calculating suggested users in a social graph, or for generating analytics reports. eg. Hadoop, and maybe Hive or HBase.
* **Platform Layer (Services)**
	* Separating the platform and web application allow you to scale the pieces independently. If you add a new API, you can add platform servers without adding unnecessary capacity for your web application tier.
	* Adding a platform layer can be a way to reuse your infrastructure for multiple products or interfaces (a web application, an API, an iPhone app, etc) without writing too much redundant boilerplate code for dealing with caches, databases, etc.

<p align="center">
  <img src="http://lethain.com/static/blog/intro_arch/platform_layer.png" alt="Platform Layer"/>
</p>
	
## Key topics for designing a system

1) **Concurrency** 
* Do you understand threads, deadlock, and starvation? Do you know how to parallelize algorithms? Do you understand consistency and coherence?

2) **Networking**
* Do you roughly understand IPC and TCP/IP? Do you know the difference between throughput and latency, and when each is the relevant factor?

3) **Abstraction**
* You should understand the systems you’re building upon. Do you know roughly how an OS, file system, and database work? Do you know about the various levels of caching in a modern OS?

4) **Real-World Performance**
* You should be familiar with the speed of everything your computer can do, including the relative performance of RAM, disk, SSD and your network.

5) **Estimation**
* Estimation, especially in the form of a back-of-the-envelope calculation, is important because it helps you narrow down the list of possible solutions to only the ones that are feasible. Then you have only a few prototypes or micro-benchmarks to write.	

6) **Availability & Reliability**
*  Are you thinking about how things can fail, especially in a distributed environment? Do know how to design a system to cope with network failures? Do you understand durability?


## Web App System design considerations:
* Security (CORS)
* Using CDN
	* A content delivery network (CDN) is a system of distributed servers (network) that deliver webpages and other Web content to a user based on the geographic locations of the user, the origin of the webpage and a content delivery server.
	* This service is effective in speeding the delivery of content of websites with high traffic and websites that have global reach. The closer the CDN server is to the user geographically, the faster the content will be delivered to the user. 
	* CDNs also provide protection from large surges in traffic.
* Full Text Search
	* Using Sphinx/Lucene/Solr - which achieve fast search responses because, instead of searching the text directly, it searches an index instead.
* Offline support/Progressive enhancement
	* Service Workers
* Web Workers
* Server Side rendering
* Asynchronous loading of assets (Lazy load items)
* Minimizing network requests (Http2 + bundling/sprites etc)
* Developer productivity/Tooling
* Accessibility
* Internationalization
* Responsive design
* Browser compatibility

## Working Components of Front-end Architecture
* Code
  * HTML5/WAI-ARIA
  * CSS/Sass Code standards and organization
  * Object-Oriented approach (how do objects break down and get put together)
  * JS frameworks/organization/performance optimization techniques
  * Asset Delivery - Front-end Ops
* Documentation
  * Onboarding Docs
  * Styleguide/Pattern Library
  * Architecture Diagrams (code flow, tool chain)
* Testing
  * Performance Testing
  * Visual Regression
  * Unit Testing
  * End-to-End Testing
* Process
  * Git Workflow
  * Dependency Management (npm, Bundler, Bower)
  * Build Systems (Grunt/Gulp)
  * Deploy Process
  * Continuous Integration (Travis CI, Jenkins)

**Links**

[How to rock a systems design interview](http://www.palantir.com/2011/10/how-to-rock-a-systems-design-interview/)

[System Design Interviewing](http://www.hiredintech.com/system-design/)

[Scalability for Dummies](http://www.lecloud.net/tagged/scalability)

[Introduction to Architecting Systems for Scale](http://lethain.com/introduction-to-architecting-systems-for-scale/)

[Scalable System Design Patterns](http://horicky.blogspot.com/2010/10/scalable-system-design-patterns.html)

[Scalable Web Architecture and Distributed Systems](http://www.aosabook.org/en/distsys.html)

[What is the best way to design a web site to be highly scalable?](http://programmers.stackexchange.com/a/108679/62739)
