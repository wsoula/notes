user-facing apis, plugins, drivers - from easiest to hardest
User Facing APIs
* all interactions with Docker go through JSON REST API
* /events endpoint is powerful for automation
* gives live external visibility on every operation the daemon is doing
  * action (continer creation)
  * something else
* interlock - github.com/ehazlett/interlock
  * event driven plugin system
  * routes events to extensions, such as HAProxy
* first docker load-balancer
  * drop in solution that runs as a container and listens for events
  * requires absolutely no change to Docker itself
* Interlock is a good example of using the api, but it might not be very useful to use now
Plugins
* process external to the docker engine that extends functionality of the docker engine
  * plugins available for volumes, networks, and authorization subsystems
  * implements well defined plugin API for the specific subsystem
  * extend single node functionality or across the cluster
  * introduced in docker 1.8
* plugin distribution is through the docker store
* plugins start and stop alongside docker engine
* plugin behavior clearly defined in a plugin manifest specification
* available in docker 1.12
* sample plugin - tiborvass/no-remove
  * simple extension of local volume driver, keeps create, mount, unount, list but implements a variation of Remove
* `docker plugin install tiborvass/no-remove`
* `docker plugin ls`
* `docker plugin disable tiborvass/no-remove`
* `docker plugin set` - pass options to plugin
* `docker plugin enable` - if you disabled it
* `docker plugin inspect`
* future - per node plugins stablized in 1.13 and swarm-deployed plugins in 1.13, beyond 1.13 customizing orchestration through plugin like node affinity, etc
Drivers
* the most work - FYI, docker daemon cannot create containers, it just passes info to containerd to run runc processes, see talk from yesterday on containerd
* in 1.12 you can replace runc with something else - introduced in a few weeks
* dockerd --add-runtime custom=/bin/my_rutime
* docker info | grep Runtime
* docker run --runtime=default busybox true
* docker run --runtime=custom busybox true
* Use Cases - since runc only starts linux containers, oracle is making runZ for Solaris.  Differet workloads, different performance/security tradeoffs - Intel Clear Containers, Hyper_ runV (hypervisor-based runtime)
