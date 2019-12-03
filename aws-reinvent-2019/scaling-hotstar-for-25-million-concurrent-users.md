Hotstar and 25 million concurrent users
---
* project hulk to load test before the actual game
  * load generation
  * performance and tsunami tests
  * chaos engineering
  * traffic pattern using ML

Streaming can use caching and doesn't make many api calls, but when everyone then goes to the homepage a lot of non-cacheable requests occur
A million users added per minute, app takes about a minute to b oot-up, 90 second reaction time (scale up or degrade), fully baked AMIs

Why they don't use auto scaling
* insufficient capacity errors (not enough capacity for that type)
* single instance type per auto scaling group
* step size of ASG - increase from 20 to 100, aws adds a few servers, then adds a few more, and then a few more, instead of all at once.  Even if you increased this would still hit api limits
* retries and exponential backoff - if error, aws waits awhile before retrying.  Removing subnet would fix that but also kill everything in that subnet
* game of (availability) zones

Battle tested scaling strategy
---
* Pre-warm infra before match time
* scale up based on request count or platform concurrency
* proactive automated scale up based on concurrency
* EC2 spot fleet - diversified instance type

Have known infra requirments for certain number of request count or platform concurrency, as it gets closer to the next value, it starts scaling in preparation

Ingredients of actual Chaos
* push notification from marketing to get more people to watch interesting match
* tsunami traffic
* delayed scale up
* bandwidth constraints
* increase latency
* network failures (CDN)

What are they looking for
* breaking point of each system
* death wave
* bottlenecks and choke points
* undiscoered issues and hidden patterns - if you don't load test at appropriate level, wont see issues at 10,000 that you will see at 1 million, even if you try to make the ratios correct
* failures at network, applications, etc

Panic mode
* turn off non-critical services - not too big a deal if 90% of ppl are watching the stream
* p0 is always up
* graceful degradation
