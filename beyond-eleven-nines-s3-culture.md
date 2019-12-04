Beyond Eleven Nines
---
* threat model
  * who is the attacked
  * what are their capabilities
  * what are they trying to do to us

* durability threat model
  * whos is the attacher - failure and decay
  * what are their capabilities - make our drives and servers fail
  * what are the trying to do to us - destroy enough hardware to lose data

* facility failure threat model
  * facility isolation - AZs
  * facility aware data placement

* hardware failure threat model
  * re-replication ("repair")
  * measure repair rates and failure rates
  * "Eleven 9s" is a function of these rates
  * track the worst case
  * auditors, measurements, and monitors and canaries to see metrics

* data corruption threat model
  * ???

* softare bug durability mechanisms
  * testing
  * zonal deployments (or smaller)

* deployment practices threat model
  * protocol versioning
  * read/write deployments - deploy version of software that can read the new version before deploying the version that can also write it
  * rollback testing

* operator error threat model
  * good tooling
    * doesn't require unnecessary input that can be inferred
    * should perform safety/sanity checks and fail safely
  * don't avoid misuse
  * ???

Organizational bvest practices
  * durability reviews
    * actual written document
    * interactive working meeting
    * review with experienced team members
    * learning opportunity for junior team members
  * root cause analysis reviews
    * common elsewhere - aviation
    * identify root cause, prioritize improvements
    * non-judgemental

Root Cause Analysis
  * what happened
  * how could it have been handled better
    * faster detection
    * better tooling
  * why did it happen
    * the root cause
    * 5 whys - act like a toddler and keep asking why to the answer of the previous question
  * what will change
    * action items
    * definitions, owners, dates

Guardrails
  * backup/restore
  * undo buffers - have an ability to undo an action you took
  * log-only deployments - deploy change that logs what it would have done instead of doing it, and then review
  * zonal deployments
