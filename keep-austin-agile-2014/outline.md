Intro
---


Jenkins Job Builder
---
* Allows the job configuration for a repo to live within the source of that repo
* Uses python under the covers
* Opensource and easy to add new plugins to
  * I am an active contributor
  * Good way to learn git and rewriting history
  * Good way to get introduced to gerrit
* Job config is written in yaml


GitHub Pull Request Builder
---


CI Monkey
---
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
