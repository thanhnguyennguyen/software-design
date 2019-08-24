<h1>Scalability Design Principles</h1>

**1. Avoid the single point of failure**

We can never just have one of anything, we should always assume and design for having at least two of everything. This adds costs in terms of additional operational effort and complexity, but we gain tremendously in terms of availability and performance under load. Also, it forces us into a distributed-first mindset. If you can’t split it, you can’t scale it has been said by various people, and it’s very true.

**2. Scale horizontally, not vertically**

There is a limit to how large a single server can be, both for physical and virtual machines. There are limits to how well a system can scale horizontally, too. That limit, though, is increasingly being pushed further ahead. Even databases are moving in that direction. Furthermore, the cost of (vertically) upgrading a server increases exponentially whereas the cost of (horizontally) adding yet another (commodity) server increases linearly.


**3. Push work as far away from the core as possible**

There are several orders of magnitude more clients than servers as we move inward into the core of our application. The less work the few have to do on behalf of the many, the better. The smaller the updates we can pass to our clients, the better.


**4. API first**

In addition to pushing work to the clients, view your application as a service with an API first. Clients these days are smartphone apps, web sites with JavaScript, and desktop applications. If the API does not make assumptions about which clients will connect to it, it will be able to serve all of them. And you open your service up for automation, as well.


**5. Cache everything, always**

Caches are essentially storages of precomputed results that we use to avoid computing the results over and over again. This is a Godsend for scalability and performance, so we must use it.

**6. Provide as fresh as needed data**

Depending on your application, users might not need the very freshest data right away. Eventual consistency leads to much better availability under the CAP theorem. If we actually need strict consistency, so be it.


**7. Design for maintenance and automation**
Software needs monitoring and updates to ensure proper operation over time. As we move out of the servers are pets era and into the servers are cattle era, our mindset has to change. Do we even need to reconfigure servers anymore? Can’t we just take old ones down and replace with new ones, that have been configured offline as part of their image creation? What monitoring data is important to us? What information does it provide us with? Do not under-estimate the time and effort spent in maintaining your application. Your initial public software release is a laudable milestone, it also marks when the real work begins.

**8. Asynchronous rather than synchronous**
We already understand asynchronous communication perfectly in the physical world. We drop off a letter in the mail, and some time later, it arrives. Until it does, we convince ourselves that it is underway, oblivious to the complexity of the postal system. We only use personal couriers for very important messages. A similar approach should be taken for our applications. Did a user just hit submit? Tell the user that the submission went well, and then process it in the background. Perhaps show the update as if it is already completely done in the mean time.


**9. Strive for statelessness**

While it may seem tempting to avoid inter-component communication by keeping track of certain state information in e.g. your application servers, don’t. Unless we host purely static pages, we can never get away from state information. We must make sure that state information is kept in as few places as possible, and within components made for it. Web and application servers are not, but distributed key-value stores are. Keeping it there lets you treat your web and application servers as completely replaceable instances, which is ideal from a scalability point of view since your server fleet can much more easily be modified when any server is able to handle any client request (despite the client being in the midst of a “session”).


**10. This too shall fail**

Computer systems fail. Software fails. Hardware fails. Designs fail. Failure handling fails! Be prepared for failure, but spare end users from witnessing it too obviously. It reflects poorly on you, even if failure is inevitable.
