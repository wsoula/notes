Keynote
---
* hashicorp learn - to learn all about each tool, free and opensource
  * terraform, consul, nomad in q4
* Vault 1.0 preview released today
  * auto unseal
  * batch tokens
  * migration between storage backends
* Vault adviser
* Nomad
  * cloud auto discovery
  * giving nodes several hours to drain themselves
* Nomad 0.9
  * Affinity - a constraint i would like, but is not hard.  affinity block in nomad file.  Might put your dependencies in here to speed up calls
  * Anti-affinity - reverse of above
  * Spreading - availability or modeling zones
  * priority scheduling
    * priority based scheduling
    * job queuing when busy
    * priority inversion - high priority work waiting on low priority work to finish
  * preemption - allow high priority to run ahead of low priority
    * system scheduler
    * service scheduler - enterprise?
    * batch scheduler - enterprise?
  * plugins
    * task drivers - how nomad executes (docker, qemu, etc)
    * device drivers - how to make nomad aware of different devices like fpga, gpu, etc
    * foundation for more plugins
    * nvidia gpu plugin
      * machine learning
      * super parallel
      * ml pipelines
* Consul
  * discovery - consul DNS
  * configuration - consul k/v
  * segmentation - consul connect
* consul connect
  * service access graph - who communicates to who, managed with cli, api, ui, terraform, etc
  * authentication? - mutual tls and certificate authority
  * data plane - actually sittingin path of data checking certificates, etc
* consul 1.4
  * built in support for envoy
  * kubernetes integration uses envoy
  * onvoy config can be modified
  * layer 7 (http, gRPC, etc)
  * revamped ACL system
    * separate "access token" from "policy"
    * policy can be restricted by DC
    * policies automatically replicated form primary dc
    * support for exact match (in addition to prefix match)
    * dc local tokens - for performance
  * multi-data center connect
    * service in DC1 can securely connect to DC2
    * intentions work across datacenters
    * CA state managed across datacenters for any provicer
    * consul enterprise
* Terraform
  * terraform 0.12 - lots of language improvements
    * for - iterate over lists and maps
    * pass resource as input or output - vpc = module.net.vpc
    * error messages are much better
  * blog post series, or live tour at conference,and 0.12 alpha is out
  * free remote state management for all terraform users - app.terraform.io/signup
  * atlantis joins hashicorp
  * remote plan and apply - terraform enterprise, for now, eventually whole community
    * integrated with sentinel
