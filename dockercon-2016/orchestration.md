* project entropy - on github- https://github.com/buildertools/entropy
* point of this was to show you dont have to do failure injection through orchestration,
  he showed how the external tool was able to maintain state by watching events (?)
* grabbed popular go api framework, created an api, and had it sit and watch for the events
  * so I think he is running a conatiner that is watching the docker events and if a new container
    is created on a different host, it will create a new container of the failure injector on the new node
