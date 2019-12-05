Runbooks
---

Risk = ipact * likelihood

runbooks
* tactical review of a situation
* description of situations that may occur
* steps to correct or enact a desired outcome
* contact list for situation

playbook - explain to c level
* strategic review or overview of situation responses
* strategic planning for future
* generally non-technical
* c-level or VP-level info
* potentially a RACIwrite a runbook for what we know
  * infrastructure - vpc resources, connectivity, on-instance
  * service - iam, s3 buckets, billing
  * application - patching, coding hole
  * other? (humans)

have to write runbooks before you can do automatic remediation

ssm-agent as a container in fargate

rra - rapid risk assessment - runbook
* finding description
* data to gather for troubleshooting
* steps to troubleshoot and fix - gather evidence before making change
* urgency
* ???

aws guard duty?
step functions

nist framework?
* notify
* detect
* protect
* respond
* recopver
* notify

risk framework template
* https://infosec.mozilla.org/guidelines/risk/rapid_risk_assessment.html

code that converts the rsult to json
* https://github.com/mozilla/rra2json

fargate incident response demo
* https://github.com/andrewkrug/fargate_ir
