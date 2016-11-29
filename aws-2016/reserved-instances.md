AWS Reserved Instances
---
* convertible - can move to equal or greater system (greater may mean more cost to get to that size)
* standard - can be regional instead of AZ
* buy -> measure -> learn
* Metrics
  * reserved coverage rate - how many hours are covered by reservations, excluding spot
  * unused reserved hours - Amount of unused (but paid for) reserved instance hours - in dollars or a percentage
* cloudability has a reserved instance planner, but it looks to be a paid thing
* 2xlarge node can be split into 2 xlarge, which can be split into 2 large, etc
* automating - cloudability has an api to get recommendations, lambda function or ruby gem, aws apis execute modifications or exchanges
* accrual accounting needed for reserved instances
  * cash basis = expense when paid
  * accrual basis - expense over time
  * when you buy reserved instances there is a large upfront cost, but then its much much cheaper in the long run
* need to amoritize you expense to show the true cost of the reserved instances
* have to re-amoritize after making modifications
* stay on top of expirations
* jr@cloudability.com
