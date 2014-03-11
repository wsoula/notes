# CI Monkey
<br><br><br>
<center>
#Will Soula
##Drilling Info<br><br>
###http://www.drillinginfo.com<br>
</center>

---

# Issues

* New repos
    * many new repos being created as we move to new platform
    * repeated work configuring jobs
* Regressions
    * broken builds from pull request merges
    * it merges cleanly but does it cause regressions
* Cowboy Coders
    * suddenly job starts failing and configuration is different
    * no way to track configuration changes

---

# CI Monkey Solutions

* New repos - automatically get ci jobs
    * enhanced to detect build type
* Regressions - repos automatically get github pull request builds
    * test the merge
* Cowbody Coders - configuration is in source control
    * Allows you to fix messed up config by just deleting the jenkins folder and running the ci-monkey
    * Allows to change config if everything is the same it can replace it in the yaml files

---

# What is Jenkins Job Builder

* opensource Jenkins job configurer created and used by openstack
* Store job configuration in code base
    * allows to see how job is configured without needing to go to jenkins
    * can have multiple sets of the same job for different branches
* Uses python under the covers
* Job config is written in yaml

---

# Features of Jenkins Job Builder

* Opensource and easy to add new plugins to
    * I am an active contributor
    * Learn git and rewriting history
    * Get introduced to gerrit
* macros for common tasks
    * pull in common macro file
    * multiple jobs per file, like the cleanup jobs
* test yaml created
    * can verify there are no syntax errors
    * aids in adding new plugin
* http://ci.openstack.org/jenkins-job-builder/

---

# How to use Jenkins Job Builder

* installation
    * http://ci.openstack.org/jenkins-job-builder/installation.html
    * test yaml script
    * update job
* configuration
    * http://ci.openstack.org/jenkins-job-builder/configuration.html
    * job
    * job template, like cleanup jobs
* commands
    * jenkins-jobs update jenkins/
    * jenkins-jobs test jenkins/ -o output

---

# How DI uses Jenkins Job Builder

* No one can manually configure a job
    * have to refer new employees to documentation about JJB
    * few people have manual configure ability
* jjb-init job
    * takes branch, repo, and org as parameters
    * runs JJB against jenkins folder
* clean cache before running JJB
* run every weekend in case configuration somehow got changed
    * few trusted people mess up
    * job left broken from jjb-init job

---

# GHPRB Workflow

- Where is it in the SDLC?
    - Starts and ends in the dev part of the SDLC
    - Small little CI loop
- What is the workflow?
    - Create your feature branch and begin work
    - Upon first commit or after tests committed open pull request
    - Continue pushing to your feature branch as normal
    - Profit from CI on a dev branch
- How to keep pull request from being accepted too soon
    - Put pull request in review card
    - Denote it is in progress in the title

---

# How To Test Codebase

- Monolithic
    - All code in one repo
    - Run like normal build
- Modules and sub-modules
    - If tests are in same repo
        - Pass sha and refspec
        - Run down stream tests against them
    - If running downstream tests
        - Publish to different location
        - Pass to repository manager (bower, ivy, maven, etc)

---

# Beyond Tests

- Deployment of documentation
    - Why
        - People without access to github
        - People not tech savvy
    - How
        - Do doc build
        - If it is a pull request figure out the pull request number
            - Change the deploy location
            - Deploy to "pr" folder
        - Deploy as normal
        - If last commit was a pull request, delete the pull request deploy

---

# Beyond Tests

- Customer demos, both internal and external
    - Deploy your latest code continuously so other dev can work on consuming your latest code (dual agile), instead of waiting for one to finish before other starts
    - If using monolithic codebase can deploy what is coming next to a site for consumption and feedback on the beta
- Comment in pull request buid number deployed in, but only if already commented
    - Get pull request number from last git message
    - Use that to comment on pull request using github api

---

# CI Monkey

* Crawls github organizations looking for repos without a jenkins folder
* Lays down a template for the type of repo it is, or a generic one if it cannot determine
* Replaces values in template
* Common tasks
    * clone from git
    * comment on pull requests
    * github url
    * creating github webhook
    * triggering main build from push
    * triggering pull request build on poll
    * put name of branch in build name

---

# CI Monkey

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

---

# Demo

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

---

# Demo

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
