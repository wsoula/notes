Enable DevOps in an Enterprise with AWS Service Catalog
---
* cloudformation
* enable self service
* AWS Service Catalog - built to manage approved templates and control access to them
* product - an IT service that you want to make available for deployment on AWS - EC2 S3
* portfolio - a collection of products, together with config info
* constraint - restrict the ways that specific AWS resources can be deployed for a product
* Stack - you know this
* service catalog
  * standardize
  * enforce consistency
  * limit access
  * enforce tagging, seecurity groups
  * one-stop shop
  * automate deployments
  * agile governance
* wiley had a subnet per web/app/cache/database
* security and separation at multiple levels
  * application
  * network
  * some third
* aws servicecatalog search-products
* aws servicecatalog describe-provising-parameters
* for prod the servicecatalog template is shared or imported into prod servicecatalog
* release mgmt create portfolios and products and adding constraints to portfolio.  Maybe make cf templates
* aws servicecatalog create-constraint
* new marketplace AMI causes new golden AMI to be created
