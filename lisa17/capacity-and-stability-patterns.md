Capacity and Stability Patterns
---
* stability - keep processing in face of impulses, stresses, or component failures
* capacity - throughput a system can sustain with acceptable response time
* Patterns
  * bulkheads - partitioning systems to prevent cascading failures
    * if you have a web app and want to run reports that could saturate the web servers, have set of
      web servers for reports and a set for regular traffic.  And if the db becomes the bottleneck, can
      separate out dbs for reports and dbs for regular traffic
  * canary testing - gradual roll out of new code
    * deploy to a subset of servers and watch the performance and errors on those servers and then decide
      if it is healthy to roll out to all servers
    * feature flags
  * graceful degradation
    * turn functionality off in repsonse to failures or load - if get a huge spike in traffic make sure
      the user can do what they came for
    * load shedding - purposefully not handling some requests in order to reserve resources for other
      * They created a waiting room, where they aren't serviced because the resources aren't there to
        support that many people
      * Sometimes they just make an event page not able to be accessed because they can't handle it and it
        might require a code fix or having the organizer change they way they are doing something
    * rate limiting - controlling the amount of work you accept
  * caching - saving and re-serving results to reduce expensive requests
    * invalidation strategies - keep it short stupid - for service calls, centralized invalidation logic -
      wrapper strategy for dynamic ttl
  * capacity planning - getting the resources you need in place, before you need them
  * timeouts
* Further Reading
  * Release It
  * Art of scalability

