Chat Ops
---

References
* (?) - https://speakerdeck.com/jnewland/chatops-at-github

What is it?
* interact with systems in chat
* hubot
* jenkins bot

Why use it?
* One place to control all systems
* Alerts cannot be ignored but can be bypassed with ease
* Everyone can see what is happening
* Everyone can see what is happening, on their first day (?)
* By placing tools directly in the middle of the conversation, everyone is pairing all the time (?)
* Teaching by doing (?)
* This was always my main motivation with hubot, teaching by making things visible.  Its an extremely powerful teaching technique (?)
* hide the ugly (?)
  * put ugly nagios ui behind shiny chatting
* Interact on mobile (?)
  * can check state of systems on the go
  * possibly fix things remotely

Bots
* hubot
  * interact with anything
  * run anywhere
* jenkins bot
  * runs in jenkins
  * few, but important, use cases

Other uses
* Drive code ownership
  * apis written for bot use
* Drive dev engagement with prod
* Possible entry-way to dev ops
* Shiny toy for people to congregate around
  * engage people bored with getting only "simple" tasks
  * keep chat rooms in forefront of peoples minds, thus uniting geographically dispersed teams
    * pop notifications
    * interesting info
* information delivery

What we have (Sparky)
* prod traffic
  * running count of unique visits a day
* automated test reports
  * runscope periodic runs
* jenkins reporting
  * build failures
  * releases
  * hipchat alert for long running job completion
* dynamic information
  * when is next release date
  * how to release code (gets default branch)
* fun
  * image me
  * lunch

Our Process
* checkin to master causes cookbook to be uploaded and chef converged

Future
* deploys (sparky switch production)
* redis for a persistent brain
* gate deploys with interactions with redis brain
