Chatops
---
* hubot - started with
* lita - now use - called spy
* Infrastructure
  * spy cd show traffic
  * spy cdn backend [region] - sends traffic to region
  * spy nginx status - shows all connections and upstream health - load balancers
  * spy profile nginx lua cpu
  * spy revisions - shows all revisions running in production
  * spy shops - print top 10 shops generating the most traffic and show which shard they are in
  * spy profile shopify
  * spy resque - shows all jobs waiting in queues - might be useful for rabbitMQ for export service
  * spy job working
  * spy shards
  * spy shard load
* Failover
  * spy failover shopify pod :pod to :location -
  * And More
    * spy chef environment :environment :server
    * spy newrelic :app
* Incident Management
  * spy incident start :incident - for ones we can't automatically find
  * spy page imoc - page the oncall with an issue - we should do this
  * spy incident tell :team :message - might be useful to let courthouse/diweb know of outages in dev
  * spy does reminders if you forget to update the status page, or close an incident or should alert others, etc
  * spy incident note - adds comment to incident - i think you can put a pencil emoji on someones message to automatically add
    it to the incident, they use slack
* Onboarding
  * spy github add user :user :team
  * spy deploy
* What if slack is down
  * I believe you can interact with spy without slack, like on itself
  * Campfire as backup chat app
