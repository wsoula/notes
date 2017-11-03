UX Design for Effective Monitoring Tools
---
* She is an observability engineer
* bit.ly/lisa17-ux
* graphite and opentsdb - make her mad
* education vs intuition - don't overload people with data - preview tool showing when in the past you would be alerted/notified
* best practices - use your expertise to determine the most helpful default behavior
* Performance - backend - roll up date over long time ranges, store latest data in memory facebooks gorilla paper
  * Add a cache layer turns splicer project
  * frontend - don't reload existing data if the user changes the time window
    * prevent the user from requesting data incessantly
    * lazy load graphs on a dashboard
* Feedback
  * search slack for words like datadog and read what people are saying
  * listen to power users that complain a lot
  * surveys every six months, on everything, with a section on monitoring tools
