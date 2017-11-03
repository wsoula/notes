Debugging @ Scale
---
* aka.ms/lisa17-debugging
* traditional tools - deugger, memory profiler, logs, wireshark (network profiler)
* some things that still work
  * error messages are still userful for users and developers
    * should give breadcrumb to help developer find issue
* distributed tracing is the new debugger
* apply machine learning (somewhere) (flycatcher?)
  * log releveant tokenization
  * negative phrase detection - 'name not resolved', 'took too long to respond', 'unable to reach'
* anomaly detection as a platform - (kibana might have something like this)
* debugging will always involve a human, otherwise its automated response
