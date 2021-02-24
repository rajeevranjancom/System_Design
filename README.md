# System Design Interview Checklist: 

 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Pic/vbnm.png" style="max-width: 100%;" alt="Welcome images" />

Usually, the System Design interviews are lengthy and cover a lot of complex components. This makes it very easy to get lost in small things and miss out on the big picture. Therefore, it becomes very important to structure your interview in a way such that you can easily convey the whole picture without wasting time on anything which does not add value.

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
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Amazon%20System%20Design.png;" alt="Welcome images" />

|  3  | [Facebook](https://github.com/rajeevranjancom/System_Design/blob/main/Facebook%20System%20Design.png) | Facebook |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Facebook%20System%20Design.png;" alt="Welcome images" />

|  4  | [Google Maps](https://github.com/rajeevranjancom/System_Design/blob/main/Google%20Maps%20Design.png) | Google Maps |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Google%20Maps%20Design.png;" alt="Welcome images" />

|  5  | [Hotel Booking](https://github.com/rajeevranjancom/System_Design/blob/main/Hotel%20Booking%20System.png) | Hotel Booking |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Hotel%20Booking%20System.png" style="max-width: 100%;" alt="Welcome images" />

|  6  | [Notification Service](https://github.com/rajeevranjancom/System_Design/blob/main/Notification%20Service%20design.png) | Notification Service |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Pic/vbnm.png" style="max-width: 100%;" alt="Welcome images" />

|  7  | [Twitter](https://github.com/rajeevranjancom/System_Design/blob/main/Twitter%20System%20Design.png) | Twitter |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Twitter%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

|  8  | [Uber System](https://github.com/rajeevranjancom/System_Design/blob/main/Uber%20System%20Design.png) | Uber System |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Uber%20System%20Design.png;" style="max-width: 100%;" alt="Welcome images" />

|  9  | [Video Streaming](https://github.com/rajeevranjancom/System_Design/blob/main/Video%20Streaming%20Platform.png) | Video Streaming |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Video%20Streaming%20Platform.png" style="max-width: 100%;" alt="Welcome images" />

|  10  | [Whatsapp](https://github.com/rajeevranjancom/System_Design/blob/main/Whatsapp%20System%20design.png) | Whatsapp |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Whatsapp%20System%20design.png;" alt="Welcome images" />

|  11  | [Zoom](https://github.com/rajeevranjancom/System_Design/blob/main/Zoom%20System%20Design.png) | Zoom |
 <img src="https://github.com/rajeevranjancom/System_Design/blob/main/Zoom%20System%20Design.png" style="max-width: 100%;" alt="Welcome images" />

