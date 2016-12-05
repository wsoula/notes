Whats new in lambda
---
* CI/CD for serverless apps
  * SAM
  * SAM in CF
  * Serverless CI/CD pipelines with AWS CodePipeline and AWS CodeBuild
* Environment Variables for lambda
* Can create immutable snapshots of your env vars
* process.env.S#_BUCKET
* SAM - common language for describing the contents of a serverless app
* CF now "speaks serverless" with native support for SAM
* New CF tools to package and deploy lambda-based apps
* export lambda blueprints and functions in SAM from the AWS Lambda console
* pipeline
  * pull source directly from github using codepipeline
  * build and package serverless with AWS CodeBuild - npm, pop, java compilations, BYO Docker
  * codepipeline integrates with cloudformation to deploy
* npm install; aws cloudformation package - to zip everything up instead of you having to do it manually
* new cloudwatch features
  * percentiles - track p99 or other percentiles in any metric
  * metrics to logs - jump from metric points directly to cloudwatch logs
* X-Ray
  * gain visibility into events travelling through services
  * trace calls and timing from lambda functions to other AWS services
  * easy configuration - when GA you wont have to do anything to get this to work, its in preview right now
  * lambda support coming soon
  * view the dynamic topology of your applications
  * see actual dependencies among microservices
  * easily detect and diagnose missing events and throttles
  *see dwell time and retries for async invokes
  * profile performance of calls your codes makes to other AWS services
* I had to leave 30 minutes early to make my next session on spot fleet
