* Run application with docker-compose -d and when you edit code it will auto redeploy, may be just mac/windows
* Splice looks like a cool sample company
* Splice runs elasticsearch in a conatiner
* docker 1.12 has orchestration built in
  * swarm mode
    * allows any engine to join any other engine and form a swarm
    * self-organizing, self-healing
    * no external data store - no key value store.  Built into each node to form consensus
    * no single point of failure
    * infrastructure-agnostic topology
  * cryptographic node identity
    * government-grade security by default
    * end to end TLS
    * built in government grade PKI
    * auto key rotation
    * revoke any node at any time
  * docker service api
    * desired state reconciliation
    * scaling
    * rolling updates
    * advanced scheduling
    * application-specified health checks
    * resheduling on node failure
  * built-in routing mesh
    * swarm-wise overlay networking
    * contianer-native load-balancing
    * DNS-based service discovery
    * no separate cluster to setup
    * works with your existing load-blaancers
    * rock-solid kernel-only data path with IPVS
    * demo
      * docker swarm init - swarm created
      * ssh to node 2 and do `docker swarm join node-1:2377`
      * docker node ls - to see nodes in swarm
      * `docker service create --name vote -p 8080:80 instavote/vote`
      * can put all nodes in cluster in loadbalancer to use existing loadbalancer like ELB because all ports are exposed
      * `docker service scale vote=6`
      * after scale containers are used with built in load balancer and round robin
      * Docker service update vote --image blah - deploy new container
      * Can do rolling update with some commands
      * If you kill a node things will heal and move to another node
  * Docker for AWS and Docker for Azure
    * Scaling Groups!  Security Groups!  SSH Keys!  All mine
    * Cf template to make swarm already exists
  * DABs
    * New portable format for multi container applications.  Its a dab
  * Demo
    * Docker deploy instavote
    * Docker service update -p 80:80
    * Container name to expose
    * Docker service tasks
    * The port expose changes elb as well
