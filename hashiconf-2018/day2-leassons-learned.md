5 Lessons Learned From Writing 300,000 lines of code
---
* Checklist for production-grade infrsatructure
  * ones we all know
    * install - have to be able to install it
    * configure - have to be able to configure it
    * provision - have to create it
    * deploy - have to update it
  * ones left behind
    * security
    * monitoring
    * logs
    * backup and restore
  * a few more
    * networking
    * HA
    * scalability
    * perforance  dynatrace, valfring, visualvm
  * no one gets to these
    * cost optimixation
    * documentation
    * tests - terratest
* gruntwork.io/devops-checklist
* Tools
  * define infra as code
  * open source and popular
  * support multiple providers
  * support reuse and composition
  * no extra infra
  * support immutable infra
  * toolset
    * terraform for basic infra
    * packer to configure the vms
    * sme of the vms form a docker cluster
    * use docker cluster to run docker containers, they just run stateless things in docker
    * under the hood: glue it all together with bash, go, and python
  * need to change behavior so people learn the tool instead of trying to bypass it and make manual changes
* Modules
  * isolation for environments
  * and for each "component" (i.e. vpc, front end app.  One deploys once a year, the ther multiple times a day.  Rate by risk level and how much its deployed)
  * break up into small reusable tested modules
  * folder per environemnt, usies modules for configuring, which can use modules themselves.  dont need to copy paste between them
  * typical repoo has /modules /examples /test
  * modules has 5 vault modules, little pieces are very important and expose input and output parameters so they can be wired together
  * tests deploy the examples to do the testing
  * build infra from small, composable modules
* Tests
  * run in completely separate account to keep from doing bad things, not even dev
  * they have cloud-nuke to cleanup things that could be left behind
  * terratest docs for info on speeding up tests
* create tag for terraform code, use that tag in each environment
