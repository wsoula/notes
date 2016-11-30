Cost Optimization at Scale
---
* goal is to pay for only what you need
* build with cost in mind
  * performance, reliability, security for the lowest cost possible
  * key cost optimization drivers at scale - autoscaling, turn off unused, periodic review, automation, target setting, limit provisiong, charge-backs, pricing models
  * five pillars - right size instances, increase elasticity, pick the right pricing model, match usae to storage class, measuring and monitoring
* right sizing
  * select cheapest instance available while meeting performance needs
  * leveraging cloudwatch metrics and setting up custom RAM metrics
* Increase Elasticity
  * lambda + cloudwatch = Automated Scheduling
  * look for dev/test, nonproduction instances that are running always-on and turn them off
  * aws.amazon.com/premiumsupport/knowledge-center/start-stop-lambda-cloudwatch
* leverage right pricing model
  * reserved instances for always on nodes
  * on-demand and spot for variable load
  * convertible RI
  * region RI
* Spot
  * spot block
  * spot fleet
* s3 - 1PB - $24,117
* s3-ia - iPB - 100% pulled - 23,xxx (2%)
* ecu - elastic compute unit
* how to implement practices at scale
  * measure and monitor - tableau? or trusted advisor
  * automating trusted advisor with aws lambda
    * trusted advisor integrated with cloudwatch metrics and then use lambda to do the needful
    * sample lambda functions will be included in the release
* center of excellence questions
  * how much of our workloa is steady state
  * why cant we reserve instances
  * are we using our account rep
  * are we reviewing our architecture (for cost?)
* establish clear targets and metrics
  * % instances turned off daily
  * % of instances right sized
  * % always-on resources covered by RI
  * % Reserved instance utilization
* companys aws cost should be evaluated as unit cost ratio - unit ost = total cost/individual or business metric
  * unit cost per customer
  * unit cost per revenue generated
  * unit cost per product or business unit
  * unit cost per internal user
* getting started
  * setup cloud competency center (person or group of people)
  * bring in right tools
  * use metrics to reinforce behavior
  * use partners to accelerate
