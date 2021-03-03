# System Design Interview Checklist: 

Usually, the System Design interviews are lengthy and cover a lot of complex components. This makes it very easy to get lost in small things and miss out on the big picture. Therefore, it becomes very important to structure your interview in a way such that you can easily convey the whole picture without wasting time on anything which does not add value.

<img src="https://github.com/rajeevranjancom/System_Design/blob/main/Pic/vbnm.png" style="max-width: 100%;" alt="Welcome images" />


# Drive the interview:

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

# Walkthrough the design:

Once you have the whole diagram ready, go over the whole design, one use case at a time and explain your design to your interviewer at a very high level. Talk about why you have chosen a particular database here and why you have used a particular mode of communication like Sync/ Async etc. You can also get into an RPC vs HTTP kind of a conversation if you made a particular design choice. You should go over what kind of data replication strategy is being used in your databases, for example, would you use a Master-Slave or a Multi Master setup etc.

# CAUTION:

Do not go into the details like APIs, DB Schema etc right away unless the interviewer asks for it. Most people get lost in designing the APIs for just one system at this point and run out of time later on.
Brownie Points: Most interviews do not have FRs and NFRs around analytics, but if your design covers that or leaves good enough scope for analytics, that elevates your solution a lot. 

# Implementation:

Once you explain the whole flow to your interviewer, ask them which component they want to discuss in detail. Usually, people do not want to go over the entire system in detail. Let them decide which is that one component that they want to dig into and then you can go over the implementation details of that particular system.

# Things you should cover here are:

APIs — Call out the APIs that this system exposes. Make sure you are using the best practices here. For example instead of a GET API with URL like GET /user/getUserbyUserId, it’s better to use: GET /user/{id}
API Protocols — You can cover what protocols are you exposing the APIs on. Most people choose REST APIs, but you can decide to use something more efficient like Thrift, Protobuf etc based on your use cases.
Events — You can call out which events this particular service listens to, who produces that event, what payload comes in, what processing happens on that event etc.

# DB Schema: 

Go over the DB Schema here. You can also get into SQL vs NoSQL debate or why have you chosen a particular database, if you did not go over the same earlier while talking about the high level design.
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

# System Design Cheatsheet:

> Picking the right architecture = Picking the right battles + Managing trade-offs

# Basic Steps:

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
	
# Key topics for designing a system:

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


# Web App System design considerations:
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

# Working Components of Front-end Architecture:
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

[interviewbit](https://www.interviewbit.com/courses/system-design/)

# SYSTEM DESIGN PREPARATION
* How to prepare for and answer system design questions

## Objective
*Learning about and implementing large-scale distributed system is not easy. I do not want to give the impression that it's something that can be learnt in a month.* 
What this repository aims to achieve, is for software engineers and students to get a rough idea of how the thought process of designing a large scale works and how big companies have managed to solve really hard problems. Along with that, there is a recent trend for companies to have an open-ended interview with system design questions, which is at times hard for engineers of all levels if they haven't gotten the opportunity to work on such systems themselves. 

This is a collection of links/documents for the following use cases:
a) Prepare for a system design or open-ended rounds.
b) Learn more about how large-scale systems work and thought process of designing a new system.

## Index
- [ ] [Starting point](#start)
- [ ] [basics](#basics)
- [ ] [How to answer in interviews](#howtoans)
- [ ] [Steps how I approach the system design questions in interviews](#myapproach)
- [ ] [Common Design questions](#designques)
- [ ] [architecture](#architecture)
- [ ] [company engineering blog links](#blog)
- [ ] [Low on time ?](#tldr)

## <a name='start'> Starting point </a>

For a very broad overview please go through these lectures, really useful:
* [Gaurav Sen's system design series](https://www.youtube.com/playlist?list=PLMCXHnjXnTnvo6alSjVkgxV-VH6EPyvoX)
Starts from simple stuff like load balancing and message queues, then moves to building full systems like Whatsapp and Tinder.

* [david malans cs75 scalability talk](https://www.youtube.com/watch?v=-W9F__D3oY4&list=PLmhRNZyYVpDmLpaVQm3mK5PY5KB_4hLjE&index=10)
Feel free to go through other lectures if needed. 

* [david huffman's talk , scaling up talk](https://www.udacity.com/course/web-development--cs253) ([Youtube link](https://www.youtube.com/watch?v=pjNTgULVVf4&list=PLVi1LmRuKQ0NINQfjKLVen7J2lZFL35wP&index=1))

* [scalability for dummies](http://www.lecloud.net/tagged/scalability)

* [Designing data intensive appliations](https://dataintensive.net/) This is by far one of the best books about large-scale systems and the practical challenges encountered during building them. It's focussed more on data-oriented applications though.

These talks should give you a starting point on how to think about such problems.

## <a name='basics'> Basics </a>

But before you begin, here are some topics(in no particular order) which in my opinion you should have a decent idea of before proceeding.

1. Operating system basics: how a file system, virtual memory, paging, instruction execution cycle etc work
(For starters silbershatz should be enough. If you already have decent knowledge try stallings book on OS)
2. Networking basics: 
Should know the TCP/IP stack, basics of how Internet, HTTP, TCP/IP work at the minimum. cs75 on youtube (1st lecture) should give a broad overview. I personally love [networking-a top down approach](http://www.amazon.com/Computer-Networking-Top-Down-Approach-Edition/dp/0132856204).
3. Concurrency basics: threads, processes, threading in the language you know. Locks , mutex etc. 
4. DB basics: types of DB's (SQL vs noSQL etc ), hashing and indexing, EAV based databases, Sharding, caching for databases, master-slave etc
5. A basic idea of how a basic web architecture is: say load balancers, proxy, servers, Database servers, caching servers, precompute, logging big data etc. Just know broadly what is each layer for.  
6. very basic summary of what the [CAP theorem](http://robertgreiner.com/2014/08/cap-theorem-revisited/) is (Have never been asked about the theorem itself, but knowing it will help you in designing large-scale systems. 

## <a name='howtoans'> How to answer in interviews </a>

* I found [hiredintech](http://www.hiredintech.com/system-design) videos an excellent place to start with. The way how to approach a design question as given in the link is really useful. It goes into how we start with clearing the use-cases of the system, then thinking in the abstract manner of the various component and the interactions. Think about the bottlenecks of the system and what is more critical for your system (eg latency vs reliability vs uptime etc) Address those giving the tradeoff of your approach. 

* [system design in crack the coding interview](http://www.flipkart.com/cracking-coding-interview-150-programming-questions-solutions-english-5th/p/itmdz4pvzbhcv6uv): good approach on how to begin attacking a problem by first solving for a small usecase then expanding the system.

* The best way to prepare for such questions is do mock interviews, pick any topic (given below) try to come up with a design and then go and see how and why it is designed in that manner. There is absolutely no alternative to practice!! Whiteboarding a system design question is similar to actually writing code and testing it! Just reading will only take you so far.

## <a name='myapproach'>Steps how I approach the system design questions in interviews</a>

These are the steps I go through mentally in the interviews, followed by actual interview experiences:

* a) **Be absolutely sure you understand the problem being asked**, clarify on the onset rather than assuming anything 
* b) **Use-cases**. This is critical, you MUST know what is the system going to be used for, what is the scale it is going to be used for. Also, constraints like requests per second, requests types, data written per second, data read per second.
* c) Solve the problem for a **very small set**, say, 100 users. This will broadly help you figure out the data structures, components, abstract design of the overall model.
* d) Write down the various components figured out so far and how will they interact with each other.
* e)  As a rule of thumb remember at least these :
 * 1. processing and servers
 * 2. storage 
 * 3. caching 
 * 4. concurrency and communication
 * 5. security 
 * 6. load balancing and proxy 
 * 7. CDN 
 * 8.  Monetization: if relevant, how will you monetize?
 eg. What kind of DB (Is Postgres enough, if not why?), do you need caching and how much, is security a prime concern? 
* f) **Special cases** for the question asked. Say designing a system for storing thumbnails, will a file system be enough? What if you have to scale for facebook or google? Will a nosql based database work?
* g) After I have my components in place, what I generally try to do is look for minor optimization in various places according to the use-cases, various tradeoffs that will help in better scaling in 99% cases.
* h) [Scaling out or up]  (http://highscalability.com/blog/2014/5/12/4-architecture-issues-when-scaling-web-applications-bottlene.html)
* i) Check with the interviewer is there any other special case he is looking to solve? Also, it really helps if you know about the company you are interviewing with, what its architecture is, what will the interviewer have more interest in based on the company and what he works on? 

## <a name='designques'> Common Design questions </a>
It generally depends what you are and you will be working on. Also what your level is but these are some of the more frequent interview questions.

* Design amazon's frequently viewed product page (eg. which shows the last 5 items you saw)
* Design an online poker game for multiplayer. Solve for persistence, concurrency, scale. Draw the ER diagram for this 
* Design a [url compression system] (http://www.hiredintech.com/system-design/the-system-design-process/)
* [Search engine](http://infolab.stanford.edu/~backrub/google.html) (generally asked with people who have some domain knowledge): basic crawling, collection, hashing etc. Depends on your expertise on this topic
* Design dropbox's architecture. [good talk on this](https://www.youtube.com/watch?v=PE4gwstWhmc)
* Design a [picture sharing website](http://highscalability.com/blog/2011/12/6/instagram-architecture-14-million-users-terabytes-of-photos.html). How will you store thumbnails, photos? Usage of CDNS? caching at various layers etc.
* * Design a news feed (eg. Facebook , Twitter): [news feed](http://www.quora.com/Software-Engineering-Best-Practices/What-are-best-practices-for-building-something-like-a-News-Feed)
* Design a product based on maps, eg hotel / ATM finder given a location. 
* Design malloc, free and [garbage collection system](http://courses.cs.washington.edu/courses/csep521/07wi/prj/rick.pdf). What data structures to use? decorator pattern over malloc etc.
* Design a site like [junglee.com](http://www.junglee.com/) i.e price comparision, availability on e-commerce websites. When and will you cache, how much to query, how to crawl efficiently over e-commerce sites, sharding of databases, basic database design
* A web application for instant messaging, eg [whatsapp](http://highscalability.com/blog/2014/2/26/the-whatsapp-architecture-facebook-bought-for-19-billion.html), facebook chat. Issues of each, scaling problems, status and availability notification etc.
* Design a system for collaborating over a document simultaneously (eg [google docs](https://neil.fraser.name/writing/sync/))
* (very common:) top 'n' or most frequent items of a running stream of data
* Design election commission architecture :
 Let's say we work with the Election Commission. On Counting day, we want to collate the votes received at the lakhs of voting booths all over the country. Each booth has a voting machine, which, when connected to the network, returns an array of the form {[party_id, num_votes],[party_id_2, num_votes_2],...}. We want to collect these and get the current scores in real time. The report we need continuously is how many seats is each party leading in. Please design a system for this.
* Design a logging system
 (For web applications, it is common to have a large number of servers running the same application, with a load balancer in front to distribute the incoming requests. In this scenario, we want to check and alarm in case an exception is thrown in any of the servers. We want a system that checks for the appearance of specific words, "Exception", "Disk Full" etc. in the logs of any of the servers. How would you design this system?)

## <a name='architecture'>Architectures :</a>

Personally I looked into the following architectures:

* [Basics of google search](http://infolab.stanford.edu/~backrub/google.html)
* Basics of messaging frameworks like Kafka , queuing architectures like rabbitmq.
* Broad overview and advantages of Redis , mongodb , cassandra. 
* [Google file system](http://static.googleusercontent.com/media/research.google.com/en//archive/gfs-sosp2003.pdf)
* [Google architecture] (http://highscalability.com/google-architecture)
* [Instagram](http://instagram-engineering.tumblr.com/post/13649370142/what-powers-instagram-hundreds-of-instances) and other image based social networks
* [Memcache scaling by facebook](https://cs.uwaterloo.ca/~brecht/courses/854-Emerging-2014/readings/key-value/fb-memcached-nsdi-2013.pdf)
* [Twitter scaling](https://www.youtube.com/watch?v=z8LU0Cj6BOU) and facebook feeds
* [facebook graph api](https://cs.uwaterloo.ca/~brecht/courses/854-Emerging-2014/readings/data-store/tao-facebook-distributed-datastore-atc-2013.pdf)
* [facebook haystack needle architecture](https://www.usenix.org/legacy/event/osdi10/tech/full_papers/Beaver.pdf)
* [youtube architecture and optimizations for video](https://www.youtube.com/watch?v=ZW5_eEKEC28)

## <a name='blog'>Company engineering blog links </a>

courtesy [checkcheckzz](https://github.com/checkcheckzz/system-design-interview#toc)

Depending on where you are interviewing, go through the company blog. VERY USEFUL IN INTERVIEWS! It really helps if you have an idea of the architecture, as the questions asked will generally be of that domain and your prior knowledge will help out here.

* [Airbnb Engineering](http://nerds.airbnb.com/)
* [Amazon](https://developer.amazon.com/blogs)
* [Amazon AWS](https://aws.amazon.com/blogs/)
* [Bandcamp Tech](http://bandcamptech.wordpress.com/)
* [BankSimple Simple Blog](https://www.simple.com/engineering/)
* [Bitly Engineering Blog](http://word.bitly.com/)
* [Cloudera Developer Blog](http://blog.cloudera.com/blog/)
* [Dropbox Tech Blog](https://tech.dropbox.com/)
* [Engineering at Quora](http://engineering.quora.com/)
* [Etsy Code as Craft](http://codeascraft.com/)
* [Facebook Engineering](https://www.facebook.com/Engineering)
* [Flickr Code](http://code.flickr.net/)
* [Foursquare Engineering Blog](http://engineering.foursquare.com/)
* [Google Research Blog](http://googleresearch.blogspot.com/)
* [Groupn Engineering Blog](https://engineering.groupon.com/)
* [High Scalability](http://highscalability.com/)
* [Instagram Engineering](http://instagram-engineering.tumblr.com/)
* [LinkedIn Engineering](http://engineering.linkedin.com/blog)
* [Oyster Tech Blog](http://tech.oyster.com/)
* [Pinterest Engineering Blog](http://engineering.pinterest.com/)
* [Songkick Technology Blog](http://devblog.songkick.com/)
* [SoundCloud Backstage Blog](https://developers.soundcloud.com/blog/)
* [Square The Corner](http://corner.squareup.com/)
* [THE REDDIT BLOG](http://www.redditblog.com/)
* [The GitHub Blog](https://github.com/blog/category/engineering)
* [The Netflix Tech Blog](http://techblog.netflix.com/)
* [Twilio Engineering Blog](http://www.twilio.com/engineering)
* [Twitter Engineering](https://engineering.twitter.com/)
* [Uber Engineering](https://eng.uber.com/)
* [Walmart Labs Tech Blog](https://medium.com/walmartlabs)
* [WebEngage Engineering Blog](http://engineering.webengage.com/)
* [Yammer Engineering](http://eng.yammer.com/blog/)
* [Yelp Engineering Blog](http://engineeringblog.yelp.com/)
* [Smarkets Blog](https://smarketshq.com/)

## <a name='tldr'>Low on time ?</a>

**I would HIGHLY recommend you do not take a shortcut unless you have a week or so for an interview. System design is best learnt by practising, shortcuts might help you in the short term, but would recommend coming back to this link for an in-depth understanding after the interview**

* a) Go through cs76 and Udacity's links given above for scaling systems. 
* b) Go through the engineering blog of the company you are interviewing in (or if its a startup go through the link of the company closest to yours)
* c) See this talk: http://www.hiredintech.com/system-design/the-system-design-process/ and develop a process for how to answer such questions.
* d) Remember these terms, just roll over them in your interview in your mind, and if relevant mention it in the interview 
 1. processing and servers
 2. storage 
 3. caching 
 4. concurrency and communication
 5. security 
 6. load balancing and proxy 
 7. CDN 
 8. Monetization

[![logo](https://github.com/rajeevranjancom/System_Design/blob/main/imgs/systemcycle.png)](https://github.com/rajeevranjancom/System_Design/blob/main/imgs/systemcycle.png)

> How to prepare system design questions for an IT company

System design is a very broad topic. Even a software engineer with many years of working experience at a top IT company may not be an expert on system design. If you want to become an expert, you need to read many books, articles, and solve real large scale system design problems.

This repository only teaches you how to handle the system design interview with a systematic approach in a short time. You can dive into each topic if you have time. Of course, welcome to add your thoughts!

## <a name='toc'>Table of Contents</a>
- [ ] [System Design Interview Tips](#tips)
- [ ] [Basic Knowledge about System Design](#intro)
- [ ] [Company Engineering Blogs](#blog)
- [ ] [Products and Systems](#system)
- [ ] [Hot Questions and Reference](#qs)
- [ ] [Good Books](#bk)
- [ ] [Object Oriented Design](#ood)

### [[⬆]](#toc) <a name='tips'>System Design Interview Tips:</a>

**Clarify the constraints and identify the user cases**

Spend a few minutes questioning the interviewer and agreeing on the scope of the system.
Remember to make sure you know all the requirements the interviewer didn't tell you about in the beginning.

User cases indicate the main functions of the system, and constraints list the scale of the system such as requests 
per second, requests types, data written per second, data read per second.

**High-level architecture design**

Sketch the important components and the connections between them, but don't go into some details. 
Usually, a scalable system includes webserver (load balancer), service (service partition), database (primary/secondary database cluster plug cache).
 
**Component design**

For each component, you need to write the specific APIs for each component. You may need to finish
the detailed OOD design for a particular function. You may also need to design the database schema for the database.

### [[⬆]](#toc) <a name='intro'>Basic Knowledge about System Design:</a>

Here are some articles about system design related topics.  

* [The Anatomy Of A System Design Interview](https://blog.pramp.com/system-design-interview-process-e91aae2dbe83)
* [How to Succeed in a System Design Interview](https://blog.pramp.com/how-to-succeed-in-a-system-design-interview-27b35de0df26)
* [How to Rock a Systems Design Interview](http://www.palantir.com/2011/10/how-to-rock-a-systems-design-interview/)
* [System Interview](http://www.hiredintech.com/app#system-design)
* [Scalability for Dummies](http://www.lecloud.net/tagged/scalability)
* [Scalable Web Architecture and Distributed Systems](http://www.aosabook.org/en/distsys.html)
* [Numbers Everyone Should Know](http://everythingisdata.wordpress.com/2009/10/17/numbers-everyone-should-know/)
* [Fallacies of distributed systems](https://pages.cs.wisc.edu/~zuyu/files/fallacies.pdf)
* [Scalable System Design Patterns](http://horicky.blogspot.com/2010/10/scalable-system-design-patterns.html)
* [Introduction to Architecting Systems for Scale](http://lethain.com/introduction-to-architecting-systems-for-scale/)
* [Transactions Across Datacenters](http://snarfed.org/transactions_across_datacenters_io.html)
* [A Plain English Introduction to CAP Theorem](http://ksat.me/a-plain-english-introduction-to-cap-theorem)
* [The CAP FAQ](https://github.com/henryr/cap-faq)
* [Paxos Made Simple](http://research.microsoft.com/en-us/um/people/lamport/pubs/paxos-simple.pdf)
* [Consistent Hashing](http://www.tom-e-white.com/2007/11/consistent-hashing.html)
* [NOSQL Patterns](http://horicky.blogspot.com/2009/11/nosql-patterns.html)
* [Scalability, Availability & Stability Patterns](http://www.slideshare.net/jboner/scalability-availability-stability-patterns)

Of course, if you want to dive into system related topics, here is a good collection of reading list about [services-engineering](https://github.com/mmcgrana/services-engineering), and
a good collection of material about [distributed systems](http://dancres.github.io/Pages/).

### [[⬆]](#toc) <a name='blog'>Company Engineering Blogs:</a>

If you are going to have an onsite with a company, you should read their engineering blog. 

* [High Scalability](http://highscalability.com/)
* [The GitHub Blog](https://github.com/blog/category/engineering)
* [Engineering at Quora](http://engineering.quora.com/)
* [Yelp Engineering Blog](http://engineeringblog.yelp.com/)
* [Twitter Engineering](https://engineering.twitter.com/)
* [Facebook Engineering](https://www.facebook.com/Engineering)
* [Yammer Engineering](http://eng.yammer.com/blog/)
* [Etsy Code as Craft](http://codeascraft.com/)
* [Foursquare Engineering Blog](http://engineering.foursquare.com/)
* [Airbnb Engineering](https://medium.com/airbnb-engineering)
* [WebEngage Engineering Blog](http://engineering.webengage.com/)
* [LinkedIn Engineering](http://engineering.linkedin.com/blog)
* [The Netflix Tech Blog](http://techblog.netflix.com/)
* [BankSimple Simple Blog](https://www.simple.com/engineering/)
* [Square The Corner](http://corner.squareup.com/)
* [SoundCloud Backstage Blog](https://developers.soundcloud.com/blog/)
* [Flickr Code](http://code.flickr.net/)
* [Instagram Engineering](http://instagram-engineering.tumblr.com/)
* [Dropbox Tech Blog](https://tech.dropbox.com/)
* [Cloudera Developer Blog](http://blog.cloudera.com/)
* [Bandcamp Tech](http://bandcamptech.wordpress.com/)
* [Oyster Tech Blog](http://tech.oyster.com/)
* [THE REDDIT BLOG](http://www.redditblog.com/)
* [Groupon Engineering Blog](https://engineering.groupon.com/)
* [Songkick Technology Blog](http://devblog.songkick.com/)
* [Google AI Blog](https://ai.googleblog.com/)
* [Google Developers Blog](https://developers.googleblog.com/)
* [Pinterest Engineering Blog](http://engineering.pinterest.com/)
* [Twilio Engineering Blog](http://www.twilio.com/engineering)
* [Bitly Engineering Blog](http://word.bitly.com/)
* [Uber Engineering Blog ](https://eng.uber.com/)
* [Godaddy Engineering](http://engineering.godaddy.com/)
* [Splunk Blog](http://blogs.splunk.com/)
* [Coursera Engineering Blog](https://building.coursera.org/)
* [PayPal Engineering Blog](https://www.paypal-engineering.com/)
* [Nextdoor Engineering Blog](https://engblog.nextdoor.com/)
* [Booking.com Development Blog](https://blog.booking.com/)
* [Microsoft Engineering Blog](https://engineering.microsoft.com/)
* [Scalyr Engineering Blog](https://blog.scalyr.com/)
* [Myntra Engineering Blog](https://medium.com/myntra-engineering)
* [Fastly Blog](https://www.fastly.com/blog/)
* [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/)
* [Lyft Engineering Blog](https://eng.lyft.com/)
* [Wish Engineering](https://medium.com/wish-engineering)
* [Doordash Engineering](https://doordash.engineering/)
* [SnowFlake Blog](https://community.snowflake.com/s/blog) 
* [Palantir Blog](https://medium.com/palantir/tech/home)

### [[⬆]](#toc) <a name='system'>Products and Systems:</a>

The following papers/articles/slides can help you to understand the general design idea of different real products and systems. 

* [MapReduce: Simplified Data Processing on Large Clusters](http://static.googleusercontent.com/media/research.google.com/zh-CN/us/archive/mapreduce-osdi04.pdf)
* [Bigtable: A Distributed Storage System for Structured Data](http://www.read.seas.harvard.edu/~kohler/class/cs239-w08/chang06bigtable.pdf)
* [The Google File System](http://static.googleusercontent.com/media/research.google.com/zh-CN/us/archive/gfs-sosp2003.pdf)
* [The Chubby lock service for loosely-coupled distributed systems](http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/en/us/archive/chubby-osdi06.pdf)
* [Dynamo: Amazon's Highly Available Key-value Store](http://www.read.seas.harvard.edu/~kohler/class/cs239-w08/decandia07dynamo.pdf)
* [Introduction to Memcached](http://www.slideshare.net/oemebamo/introduction-to-memcached)
* [Cassandra Introduction Features](http://www.slideshare.net/planetcassandra/cassandra-introduction-features-30103666)
* [Introduction to HBase](http://www.slideshare.net/alexbaranau/intro-to-hbase)
* [Introduction to MongoDB](http://www.slideshare.net/mdirolf/introduction-to-mongodb)
* [Introduction to Redis](http://www.slideshare.net/dvirsky/introduction-to-redis)
* [Storm](http://www.slideshare.net/previa/storm-16094009)
* [Introduction to Zookeeper](http://www.slideshare.net/sauravhaloi/introduction-to-apache-zookeeper)
* [Kafka](http://www.slideshare.net/mumrah/kafka-talk-tri-hug)
* [YouTube Architecture](http://highscalability.com/youtube-architecture)
* [Scaling Pinterest](http://highscalability.com/blog/2013/4/15/scaling-pinterest-from-0-to-10s-of-billions-of-page-views-a.html)
* [Google Architecture](http://highscalability.com/google-architecture)
* [Scaling Twitter](http://highscalability.com/scaling-twitter-making-twitter-10000-percent-faster)
* [The WhatsApp Architecture](http://highscalability.com/blog/2014/2/26/the-whatsapp-architecture-facebook-bought-for-19-billion.html)
* [Flickr Architecture](http://highscalability.com/flickr-architecture)
* [Amazon Architecture](http://highscalability.com/amazon-architecture)
* [Stack Overflow Architecture](http://highscalability.com/blog/2009/8/5/stack-overflow-architecture.html)
* [Pinterest Architecture](http://highscalability.com/blog/2012/5/21/pinterest-architecture-update-18-million-visitors-10x-growth.html)
* [Tumblr Architecture](http://highscalability.com/blog/2012/2/13/tumblr-architecture-15-billion-page-views-a-month-and-harder.html)
* [Instagram Architecture](http://highscalability.com/blog/2011/12/6/instagram-architecture-14-million-users-terabytes-of-photos.html)
* [TripAdvisor Architecture](http://highscalability.com/blog/2011/6/27/tripadvisor-architecture-40m-visitors-200m-dynamic-page-view.html)
* [Scaling Mailbox](http://highscalability.com/blog/2013/6/18/scaling-mailbox-from-0-to-one-million-users-in-6-weeks-and-1.html)
* [Salesforce Architecture ](http://highscalability.com/blog/2013/9/23/salesforce-architecture-how-they-handle-13-billion-transacti.html)
* [ESPN Architecture](http://highscalability.com/blog/2013/11/4/espns-architecture-at-scale-operating-at-100000-duh-nuh-nuhs.html)
* [Uber Architecture](http://highscalability.com/blog/2015/9/14/how-uber-scales-their-real-time-market-platform.html)
* [DropBox Design](https://www.youtube.com/watch?v=PE4gwstWhmc)
* [Splunk Architecture](http://www.splunk.com/view/SP-CAAABF9)

### [[⬆]](#toc) <a name='qs'>Hot Questions and Reference:</a>

There are some good references for each question. The references here are slides and articles. 

**Design a CDN network**  
Reference:  
* [Globally Distributed Content Delivery](https://kilthub.cmu.edu/articles/journal_contribution/Globally_distributed_content_delivery/6605972)

**Design a Google document system**  
Reference:  
* [google-mobwrite](https://code.google.com/p/google-mobwrite/)
* [Differential Synchronization](https://neil.fraser.name/writing/sync/)

**Design a random ID generation system**  
Reference: 
* [Announcing Snowflake](https://blog.twitter.com/2010/announcing-snowflake) 
* [snowflake](https://github.com/twitter/snowflake/)

**Design a key-value database**  
Reference:   
* [Introduction to Redis](http://www.slideshare.net/dvirsky/introduction-to-redis)

**Design the Facebook news feed function**   
Reference:   
* [What are best practices for building something like a News Feed?](http://www.quora.com/What-are-best-practices-for-building-something-like-a-News-Feed) 
* [What are the scaling issues to keep in mind while developing a social network feed?](http://www.quora.com/Activity-Streams/What-are-the-scaling-issues-to-keep-in-mind-while-developing-a-social-network-feed) 
* [Activity Feeds Architecture](http://www.slideshare.net/danmckinley/etsy-activity-feeds-architecture)

**Design the Facebook timeline function**   
Reference: 
* [Building Timeline](https://www.facebook.com/note.php?note_id=10150468255628920) 
* [Facebook Timeline](http://highscalability.com/blog/2012/1/23/facebook-timeline-brought-to-you-by-the-power-of-denormaliza.html)

**Design a function to return the top k requests during past time interval**   
Reference:  
* [Efficient Computation of Frequent and Top-k Elements in Data Streams](http://www.cse.ust.hk/~raywong/comp5331/References/EfficientComputationOfFrequentAndTop-kElementsInDataStreams.pdf)
* [An Optimal Strategy for Monitoring Top-k Queries in Streaming Windows](http://davis.wpi.edu/xmdv/docs/EDBT11-diyang.pdf)

**Design an online multiplayer card game**   
Reference:  
* [How to Create an Asynchronous Multiplayer Game](http://www.indieflashblog.com/how-to-create-an-asynchronous-multiplayer-game.html)   
* [How to Create an Asynchronous Multiplayer Game Part 2: Saving the Game State to Online Database](http://www.indieflashblog.com/how-to-create-async-part2.html)  
* [How to Create an Asynchronous Multiplayer Game Part 3: Loading Games from the Database](http://www.indieflashblog.com/how-to-create-async-part3.html)  
* [How to Create an Asynchronous Multiplayer Game Part 4: Matchmaking](http://www.indieflashblog.com/how-to-create-async-part4-html.html#comment-4447)  
* [Real Time Multiplayer in HTML5](http://buildnewgames.com/real-time-multiplayer/)  

**Design a graph search function**   
Reference:   
* [Building out the infrastructure for Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-building-out-the-infrastructure-for-graph-search/10151347573598920)
* [Indexing and ranking in Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-indexing-and-ranking-in-graph-search/10151361720763920) 
* [The natural language interface of Graph Search](https://www.facebook.com/notes/facebook-engineering/under-the-hood-the-natural-language-interface-of-graph-search/10151432733048920) and [Erlang at Facebook](http://www.erlang-factory.com/upload/presentations/31/EugeneLetuchy-ErlangatFacebook.pdf)

**Design a picture sharing system**   
Reference:   
* [Flickr Architecture](http://highscalability.com/flickr-architecture) 
* [Instagram Architecture](http://highscalability.com/blog/2011/12/6/instagram-architecture-14-million-users-terabytes-of-photos.html)

**Design a search engine**   
Reference:  
* [How would you implement Google Search?](http://programmers.stackexchange.com/questions/38324/interview-question-how-would-you-implement-google-search)  
* [Implementing Search Engines](http://www.ardendertat.com/2012/01/11/implementing-search-engines/)

**Design a recommendation system**  
Reference:  
* [Hulu’s Recommendation System](http://tech.hulu.com/blog/2011/09/19/recommendation-system.html)  
* [Recommender Systems](http://ijcai13.org/files/tutorial_slides/td3.pdf)

**Design a tinyurl system**    
Reference: 
* [System Design for Big Data-tinyurl](http://n00tc0d3r.blogspot.com/) 
* [URL Shortener API](https://developers.google.com/url-shortener/?csw=1)

**Design a garbage collection system**    
Reference:   
* [Baby's First Garbage Collector](http://journal.stuffwithstuff.com/2013/12/08/babys-first-garbage-collector/)
 
**Design a scalable web crawling system**    
Reference:  
* [How can I build a web crawler from scratch?](https://www.quora.com/How-can-I-build-a-web-crawler-from-scratch)

**Design the Facebook chat function**    
Reference:   
* [Erlang at Facebook](http://www.erlang-factory.com/upload/presentations/31/EugeneLetuchy-ErlangatFacebook.pdf)  
* [Facebook Chat](https://www.facebook.com/note.php?note_id=14218138919&id=9445547199&index=0)

**Design a trending topic system**    
Reference:  
* [Implementing Real-Time Trending Topics With a Distributed Rolling Count Algorithm in Storm](http://www.michael-noll.com/blog/2013/01/18/implementing-real-time-trending-topics-in-storm/)   
* [Early detection of Twitter trends explained](http://snikolov.wordpress.com/2012/11/14/early-detection-of-twitter-trends/)
 
**Design a cache system**    
Reference:   
* [Introduction to Memcached](http://www.slideshare.net/oemebamo/introduction-to-memcached)

### [[⬆]](#toc) <a name='bk'>Good Books:</a>

* [Big Data: Principles and best practices of scalable realtime data systems](http://www.amazon.com/Big-Data-Principles-practices-scalable/dp/1617290343)
* [Real-Time Analytics: Techniques to Analyze and Visualize Streaming Data](http://www.amazon.com/Real-Time-Analytics-Techniques-Visualize-Streaming/dp/1118837916)
* [Building Microservices: Designing Fine-Grained Systems](http://www.amazon.com/Building-Microservices-Sam-Newman/dp/1491950358)
* [Designing Data-Intensive Applications: The Big Ideas Behind Reliable, Scalable, and Maintainable Systems](https://www.amazon.com/Designing-Data-Intensive-Applications-Reliable-Maintainable/dp/1449373321)

### [[⬆]](#toc) <a name='ood'>Object Oriented Design:</a>

#### Tips for OOD Interview

**Clarify the scenario, write out user cases**

Use case is a description of sequences of events that, taken together, lead to a system doing something useful. Who is going to use it and how they are going to use it. The system may be very simple or very complicated.

Special system requirements such as multi-threading, read or write oriented.

**Define objects**

Map identity to class: one scenario for one class, each core object in this scenario for one class.

Consider the relationships among classes: certain class must have unique instance, one object has many other objects (composition), one object is another object (inheritance).

Identify attributes for each class: change noun to variable and action to methods.

Use design patterns such that it can be reused in multiple applications.

#### Useful Websites

* [101 Design Patterns & Tips for Developers](http://sourcemaking.com/design-patterns-and-tips)






Best of luck :+1:, feel free to send pull requests to add more content to this git!
