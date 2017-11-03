Distributed Tracing
---
* tracing requests across distributed system boundaries
* white box tracing
  * metadata propagations
    * dapper - inspired zipkin
    * zipkin
* How
  * tracer
  * transport
  * collector
  * storage
  * ui
* Tracer
  * lives inside your apps, does the tracing
  * trace - whole story of going all the way through the system
  * Span - discrete piece of work within the trace
  * parent child relationship in header to show flow of request instead of relying on timestamps
  * should have tag for service receive and service send so can get network time as well as app time
* OpenSource
  * jaeger
  * zipkin
* Opentracing is a standardized concept so switching vendors for tracing is fairly easy
* What others are doing - Jonathan Mace, Brown University
