Intro
---
* Many new repos being created as we move to new platform
* Tired of broken builds from pull request merges
  * test early and often
  * test the merge
* Problems with jobs not being configured the way I thought they were and trying to figure out how they were changing
  * Do not care what the configuration of the job is, because it is in source control
    * Can always get back to working config if someone changes it
    * No one can manually configure the job
      * have to continuously tell new people they cannot manually configure the job
      * send them to documentation about how we use JJB
* Tired of having to do the same thing over and over as the build guy
  * created ci-monkey to keep from having to make the same changes over and over (drop yaml file and replace values)
  * enhanced ci-monkey to detect build to keep from having to change repo the same way over and over (change build to actually build, version format)



Jenkins Job Builder
---
* Allows the job configuration for a repo to live within the source of that repo
* Uses python under the covers
* Opensource and easy to add new plugins to
  * I am an active contributor
  * Good way to learn git and rewriting history
  * Good way to get introduced to gerrit
* Job config is written in yaml
* http://ci.openstack.org/jenkins-job-builder/
* macros for common tasks
  * pull in common macro file
  * multiple jobs per file, like the cleanup jobs
* installation
  * http://ci.openstack.org/jenkins-job-builder/installation.html
  * test yaml script
  * update job
* configuration
  * http://ci.openstack.org/jenkins-job-builder/configuration.html
  * job
  * job template, like cleanup jobs


GitHub Pull Request Builder
---
* pull in presentation from JUC 2013


CI Monkey
---
* Crawls github organizations looking for repos without a jenkins folder
* Lays down a template for the type of repo it is, or a generic one if it cannot determine
* Replaces values in template
* Lays down three jobs
  * one to build the HEAD of a repo
    * HEAD on a freshly cheked out repo is the default branch
    * Always wipe the workspace on clone
    * Allows to change branch being built by changing the default branch in github and wiping the job workspace
  * one to build pull requests
    * Can run just tests
    * Could publish for further testing of pull request
    * Run JJB if changing jenkins folder
  * one to run JJB
    * pull request runs this too but the change
    * After this build runs, run the main build to make sure config changes did not break build


Demo
---
* Start with brand new machine with no jenkins or JJB on it
* Install JJB and download jenkins and start jenkins
* Create jjb-init job with jenkins job builder
* Use jjb-init to create ci-monkey
* Create play repo with play create and push to github
  * Run ci-monkey and see jobs created
* Create cookbook repo and push to github
  * Run ci-monkey and see jobs created
* Create grunt repo and push to github
  * Run ci-monkey and see jobs created
* Create ant build and push ot github
  * Run ci-monkey and see jobs created but placeholder build
* Open pull request with changes to code that causes test failures
  * See pull request run and comment with test results
  * Fix code to not fail tests and push to feature branch and see tests pass
* Open pull request with changes to documentation
  * See pull request run and publish to pull request site
* Open pull request with changes to code
  * See pull request run and publish changes to pull request site, or ability to dl executable
* Open pull request with change to JJB
  * See JJB change in configuration
  * rerun JJB job to set configuration back to original setting
* Straight commit change to JJB to repo
  * See JJB job run and reconfigure job then run the main build
