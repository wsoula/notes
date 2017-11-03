Pintrace - Distributed Tracing
---
* annotation - span - trace
* span is the hop from one service to another
* structured logging on steroids
* pintrace - zipkin based tracing solution
* challenge 1 - build instrumentation
* challenge 2 - span report and aggregation
* challenge 3 - deploy instrumentation
  * sample <1% of traffi
* tracing through cdn
* applications of trace data
  * improve time to triage
    * automated RCA
    * tracking down p99 latencies
  * Identify architectural optimizations
  * latency pipeline
  * inter AZ traffic analysis
* Lessons Learned
  * user awareness and education are very important to making tracing successful
  * being with the end in mind
  * trace most valuable path in the app
  * distributed tracing landscape is confusing
  * quality of traces is more important than quantity
* tinyurl.com/pintrace-achitecture
* tinyurl.com/pintrace-applications
* tinyurl.com/pintrace-analysis
