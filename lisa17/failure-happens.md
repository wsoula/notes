Failure Happens - Improving Incident Response in Enterprise
---
* value stream mapping
* mttd - mean time to detect
  * all that really matters is you detecting it before your customers
  * better is mean time to diagnose
  * if you see someone on the ground that is detecting the problem, but its better to know if the person is dead, or asleep, etc
* mttr - mean time to restore
  * better is mean time to repair - fixing underlying problem so it won't happen again
* Cost - head count involved
  * better is people involved in context wagon - people following the problem or on the email chain as more
    and more people are dragged in
* empower those closest to the issue
  * silos get in the way
* Steps to establish operations as a service
  * step 1 - establish secure ops hub - (rundeck?)
  * step 2 - establish a sdlc for ops procedures
  * step 3 - connect with enterprise managment systems
* Encourage Developers to think operable first
  * operations is the business (unless you literally sell packaged software)
  * deployability, sonfigurability, monitoring are service features
  * build configurablity into the service, don't externalize it
  * demand "prod-like" environments everywhere
  * ake any handoff between teams "verification driven"
  * create immutable versioned things
* key is to push ability to take action closest to the problem
