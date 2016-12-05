Lessons Learned from a Year of Using Spot Fleet
---
* yelp sponsor
* Seagull - runs tasks for yelp, they created it - unit.integration, and acceptance tests (Runs >25 million a day)
  * built on top of apache mesos
  * originally on-demand
  * then spot, which has instability
  * then spot fleet
* spot fleet
  * when one regions spot price goes beyond limit, then it spins up new ones in the other regions
  * can still run into issue with all azs fluctuating and you cant get your capacity
    * they dealt with it by going into 30 spot markets instead of 3, which i assume means multiple regions
    * or try a different instance type - but it may take longer or not perform as well (is that the same thing?)
  * be simple and dont bid too high
  * diversify spot markets
* FleetMiser - auto scaling engine - yelps in-house scaling engine
  * stores metrics and monitoring in other services in order to affect the scaling signals
* Autoscaling Signals
  * cluster underutilized - scale down
  * developers submitted batch jobs, maintain capacity/scale up
  * cluster overutilized - scale up
  * historical usage indicates demand - scale up
* Spin up by getting cheapest possible, or you can scale up using diversification to avoid losing nodes
* sounds like spot fleet can replace our ASGs, but we arent spread across AZs to do that from I understand how they do it, maybe they mean having several instance types in the cluster, so like a c3.large, c3.xlarge, c3.4xlarge for geoserver, treat 1vcpu as 1 unit and then they can compare like that
* when scaling down they determine what instances to scale down, dont let amazon do it
* Amazon has auto scaling for spot fleets - http://aws.amazon.com/blogs/new-auto-scaling-for-ec2-spot-fleets
  * spot fleet scaling
    * driven by cloudwatch metrics, 
    * policies can scale by constant, percentage, step function
    * no customer scale-down logic
    * an easy way to get your cluster autoscaling
  * fleet miser scaling
    * custom signal plugins
    * scaling by arbitrary amounts (based on signal input)
    * specify instances to terminate
    * aloows for more complicated functionality
* future of seagull and fleetmiser
  * diversify spot markets even further
    * X1.32XLarge
    * P2.16XLarge
    * so i guess they diversify by instance type, not az
  * more advanced scaling logic for fleetmiser
    * combine and control multiple spot fleets and ASGs at once
    * extend scale down logic
* i guess find what number of units are required for each server and then add several types that encompass that, an overprovisioned spot instance is cheaper than a right size on demand, but youll keep trying to get back to the right size spot
* better scheduling of tasks
