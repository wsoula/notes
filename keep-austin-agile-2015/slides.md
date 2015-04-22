# How to Put Information in the Middle of the Conversation to Bring Teams Together

<br><br><br>
![right](kaa-theme/images/intro-slide3.jpg)
<center>
#Will Soula
##Drilling Info<br><br>
###http://www.drillinginfo.com<br>
</center>

---
Chat Ops
---

References
* (?) - https://speakerdeck.com/jnewland/chatops-at-github

* What is Chat-Ops and how and why to use it
<br><br>

* See how DI uses chat ops everyday
<br><br>

* How DI extends hubot and deploys it
<br><br>

* Future Plans at DI for chat ops

---
Sparky
---
<img src="hip-chat-screenshot.png" alt="Sparky" style="height: 500px;"/>

---
Sparky
---
<img src="hip-chat-screenshot2.png" alt="Sparky" style="height: 500px;"/>

---
What is Chat-Ops?
---
<br><br>

* Interact with systems in chat
<br><br>

* Information in the middle of the conversation
<br><br>

* Teaching by doing

---
Why Use Chat-Ops?
---
* One place to control all systems
* Alerts cannot be ignored but can be bypassed with ease
* Github presentation (FIXME)
    * Everyone can see what is happening
    * Everyone can see what is happening, on their first day
    * By placing tools directly in the middle of the conversation, everyone is pairing all the time
    * Teaching by doing
    * This was always my main motivation with hubot, teaching by making things visible.  Its an extremely powerful teaching technique
    * hide the ugly
        * put ugly nagios ui behind shiny chatting
---
Why Use Chat-Ops?
---
<br><br><br>

* Interact on mobile
    * can check state of systems on the go
    * possibly fix things remotely
---
How chat ops makes teams more agile
---
* All information gathered from systems in the agile process
    * rally/kanbanery/jira
    * jenkins/travis/teamcity
    * svn/git/cvs
    * datadog/newrelic/uptime
* feedback loop of best practices
    * see what other people are doing
    * help others get better
* increase throughput of work, no waiting
    * instantly see work ready for review
    * catch mistakes earlier
---
Technology Required
---
* Bot
    * hubot
        * interact with anything
        * run anywhere
    * jenkins bot
        * runs in jenkins
        * few, but important, use cases
    * services
        * github
        * datadog
---
Technology Required
---
* Chat server/client and room
    * hipchat
    * slack
    * jabber

---
Other uses
---
* Drive code ownership
    * apis written for bot use
* Drive dev engagement with prod
* Possible entry-way to dev ops
---
Other Uses
---
* Shiny toy for people to congregate around
    * engage people bored with getting only "simple" tasks
      * put an api in your work and get info from it to the chat room
      * extend bot to do other tasks or do your tasks for you
  * keep chat rooms in forefront of peoples minds, thus uniting geographically disperse teams
      * pop notifications
      * interesting info
* information delivery
---
What DI Has (Sparky)
---
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
---
What DI Has (Sparky)
---
* fun
    * image me
    * lunch
---
Our Process
---
* open pull request with changes to hubot
* checkin to master causes cookbook to be uploaded and chef converged
---
Future for DI
---
* deploys (sparky switch production)
* redis for a persistent brain
* gate deploys with interactions with redis brain
* asks people to review/cleanup work
    * review pull request that is old and stale
    * asks to close pull request that is old and stale
    * asks to delete unused nodes/clients/cookbooks/repos/artifacts
