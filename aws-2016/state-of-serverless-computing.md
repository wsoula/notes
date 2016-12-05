State of Serverless Computing
---
* lamba isnt the only serverless service they have
  * s3, dynamodb, amazon api, etc
* How to debug lambda?  No logs how to see why it is failing? - pretty certain there are logs
* common use cases
  * web applictions - express and flask, open source, recently released
  * back ends - apps & services, mobile, IoT
  * data processing - real time, mapreduce, batch
  * amazon alexa - powering voice enabled apps, alexa skills kit
  * chatbots - powering chatbot logic (lex?)
  * easiest way to build a webhook is lambda
* Herd to manage s3
* API Gateway has full fidelity swagger specs
* Lex will soon have slack integration
* Lambda event sources
  * api gateway, s3, dynamodb, aurora, sns, ses, cognito, cloudwatch, kinesis, codecommit, cloudformation, config, lex
  * idea was to trigger alert if server terminated without it being a user initiated action, but i think they all are
* Amazon API Gateway listings in the AWS Marketplace - post api endpoints to aws marketplace
* can make a cool lambda function, add to your API Gateway, and then you can make money on it in the marketplace
* Dead letter Queues
  * automatically capture events after exhausting retries
  * build even more reliable event processing
  * target amazon sqs queues or amazon sns topics
  * thus if you function fails three times it goes to the queue which can trigger another lambda function to do error handling
* SAM - severless application model
  * standard model for representing serverless applications on AWS
  * functions, apis, event sources, and data stores
  * simplifies deployment and management for serverless applications
  * natively supported by cf
  * export any function as a SAM template
  * package and deploy SAM templates using AWS CLI
  * open spec under apache 2.0 for community extensions - can download sam from github
  * AWS CodePipeline + SAM
    * github
    * AWS CodeBuild - can do the piping and other dependency as well - build
    * AWS CodeBuild third party tools - test
    * AWS CodePipeline integrates with CF to deploy to prod
* How do you debug distributed applications made of multiple functions or services
* How do you gain insights into how your functions are performing or behaving
* Answer is AWS X-Ray
  * analyze and debug distributed apps in prod
  * visualize service call graph of your app
  * identify performance bottlenecks and errors
  * pinpoint service-specific issues
  * identify impact of issues on users of the app
  * lambda support coming soon
* AWS Step Functions
* Lambda is now available in all AMazon CloudFront edge locations
* AWS Greengrass
  * extends AWS processing on devices
  * low latency, newar-real time
  * can add lambda to devices now, if you dont have access to the cloud
