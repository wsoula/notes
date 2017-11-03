Queueing Theory
---
* on speakerdeck somewhere emfree (?)
* queueing theory gives a vocabulary and toolkit to talk about systems
* Serial Systems
  * Service - recieves data from customers, highly concurrent, mostly cpu-bound, low-latency
  * how do we allocate appropriate resources for this service?
  * production scale load testing is time consuming bt would work well
  * small expermients plus modelling
  * Question: what's he maximal singlec-ore throughput of the service
  * Can we identify a model for this
  * Step 1 Identify the question
    * the busier the server is, the longer is takes to respond
  * Step 2 Identify assumptions about our system
    * takes arrive independently and randomly at an average rate lambda
    * the server takes a constant time s, the service time, to process each task
    * the server processes one task at a time
  * Step 3 draw a picture of the system over time
    * At any given time, how much unfinished work is at the server
    * If throughput is low, tasks complete before new one comes in
    * But as throughput increases, tasks may have to wait
    * Remember, we care about average wait time
    * Two ways
      * average width of blue parallelograms
      * average height of the graph
    * Idea - relate area under graph and avg height
* Parallel Systems
  * depends on how we assign incoming tasks
  * assuming optimal assignment of tasks to servers, opetimal assignment is not free
* Lessons:
  * making scale-invariant decisions...
  * But something else is pretty good
