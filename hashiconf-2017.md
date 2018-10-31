Consul
---
* Can discover servers using instance metadata.  He said you could
  specify aws and then tags so you can find consul by the tag.  He
  even talked about having the servers in an ASG and then finding
  them this way
* Network Segments allows you to basically have multiple clusters but one
  group of shared consul servers.  Enterprise only
* Fabio - register service with consul and add tag url-prefix-drillinginfo.com/example
  and it knows /example goes to that service
* Consul can lock kv and then unlock if the node with the lock dies
* Can use external service by specifying the address instead of just the port
* Feature Toggle - can set key called newfeature1/host1 where host1 is a hostname (maybe service?)
  and then in the service code do if consul.Get(newfeature1/$hostname) == true { feature }
* Prepared Queries - define which service to lookup and what order to look them up and what to do
  if none available.  /v1/query endpoint, use prepared query template (Type: name_prefix_match) Failover: ["US","EU"]
  Does it make any sense to do failover from dev to prod?  Especially if we want to scale dev down at night.
  Or does that make too much concern about cross talk

Nomad
---
* Cluster of one can be used to test your job file locally
* Nomad allows an artifact block that can download config/tars/etc
* Nomad template section can read ENV or key/value from consul
* In 0.7 health based restarting and web UI
* Rolling deployments allow you to verify the job template, and it came up
  with optional ability to auto revert
* Canary will place canaries out there and not touch existing allocations till
  you tell it you are ready to deploy
* Nomad Plan allows a dry run of a job update `nomad run`
* Telemetry built in - one presenter sent to statsite
* Look into running locally, possibly with raw_exec, to test upgrades.  They
  used a monolithic docker image with full stack
* HEALTH (From pager duty nomadic journey talk)
  * separate cluster and put apps in it or canary apps that stress the system
    * Canary - server - respond to /ping willingly terminates
               client -
  * injecting failures - http://pagerduty.com/blog/failure-friday-at-pagerduty
  * telemetry? (Not in talk, but an idea i have)

Terraform
---
* Estate from under armour is a ui for terraform
* terraformctl (opensource)
