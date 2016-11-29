Riot Games AWS
---
* security monkey and trusted advisor for auditing
* scaled total ownershio on AWS with EC2 and ECS and terraform
* docker - artifactory to run internal docker container host
* first iteration used asgard which is now spinnaker
* elastic beanstalk can do some docker stuff
* second iteration was kubernetes; mesosphere has cf templates
* third iteration used ECS AMI and is designed with AWS integration in mind, and its free
* ECS has service scaling to automatic task count scaling based on cloudwatch metrics introduced
* can use task specific IAM roles instead of setting it at the cluster (host?) level; i.e. service a can get access to s3 but service b cant
* application load balancers (ALB)
* terraform AWS blog
* use remote state files like putting it in s3 since it contains passwords and such and it should match the terraform code so it doesnt need to be checked in
* tag everything all of the time, keep your tags organized in your terraform templates, have a top level variable that get applied to every resource, create a tag for every dimension that is useful to your business, i.e. what we already have, env-service
* profile your memory requirements, monitor for scheduling issues
* engineering.riotgames.com
