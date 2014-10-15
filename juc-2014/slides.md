#<br>
<br><br><br>
<center>
#![right](theme/images/juc_title.jpg)
<br>
#Will Soula
##Drilling Info
###http://www.drillinginfo.com<br>
<br>
###October 23, 2014
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

* New repos - automatically get ci jobs (CI Monkey)
    * enhanced to detect build type
* Regressions - repos automatically get github pull request builds (GHPRB)
    * test the merge
* Cowbody Coders - configuration is in source control (JJB)
    * Allows you to fix messed up config by just deleting the jenkins folder and running the ci-monkey
    * Allows to change config if everything is the same it can replace it in the yaml files

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

# What is Jenkins Job Builder

* Opensource Jenkins job configurer created and used by openstack
* Store job configuration in code base
    * allows to see how job is configured without needing to go to jenkins
    * can have multiple sets of the same job for different branches
* Uses Python under the covers
* Job config is written in yaml

---

# Features of Jenkins Job Builder

* Opensource and easy to add new plugins to
    * I am an active contributor
    * Learn Git, Gerrit and rewriting history
* Macros for common tasks
    * pull in common macro file
    * multiple jobs per file 
* Test yaml created
    * can verify there are no syntax errors
    * aids in adding new plugin
* Templates for common jobs
    * like macros but for entire jobs
    * multiple jobs per file

---

# How to use Jenkins Job Builder

Installation:

* install python
* clone from github
* sudo python setup.py install

Configuration (/etc/jenkins_jobs/jenkins_jobs.ini):

    !properties
    [jenkins]
    user=USERNAME
    password=PASSWORD
    url=JENKINS_URL
    ignore_cache=IGNORE_CACHE_FLAG

---

# Job Configuration with JJB

Job

    !yaml
    - job
        name: test-job
        description: A test job of JJB
        project-type: freestyle
        properties:
          - github:
              url: https://git.drillinginfo.com/DIGlobal/map-widget/
        scm:
          - git:
              url: ssh://git@git.drillinginfo.com/DIGlobal/map-widget.git
              branches:
                - "$default_branch"
              wipe-workspace: true
              browser: githubweb
              browser-url: https://git.drillinginfo.com/DIGlobal/map-widget/
              git-tool: System Default Git
        triggers:
          - github
          - pollscm: ''
        builders:
          - shell: |
                   echo Hello World
        wrappers:
          - build-name:
              name: ${ENV,GIT_BRANCH"}-#$BUILD_NUMBER

---

# Macro Use with JJB

Macro

    !yaml
    - builder:
        name: builder-macro
        builders:
            - shell: |
                     echo "You passed {task}"
    - job
        name: test-macroA
        description: A test of echoing foo
        project-type: freestyle
        builders:
          - builder-macro:
              task: foo
    - job
        name: test-macroB
        description: A test of echoing bar
        project-type: freestyle
        builders:
          - builder-macro:
              task: bar

---

# Job Template Use with JJB

Job Template, like macro but for entire job:

    !yaml
    - builder:
        name: ant-build
        builders:
            ant: "{targets}"
    - job-template:
        name: "{name}-build"
        description: Build the {name} project
        project-type: freestyle
        builders:
          - ant-build:
              targets: "test"
    - job-template:
        name: "{name}-jjb"
        description: Build the {name} gradle build
        project-type: freestyle
        builders:
          - ant-build:
              targets: "jjb"
                    
    - project:
        name: testAnt
        jobs:
          - '{name}-build'
          - '{name}-jjb'

---

# How to use JJB

Commands

* jenkins-jobs update jenkins/
* jenkins-jobs test jenkins/ -o output
* update Jenkins Job Builder itself

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
    * one to build the default branch of a repo
        * Always wipe the workspace on clone
        * Allows to change branch being built by changing the default branch in github
    * one to build pull requests
        * Can run just tests
        * Could publish for further testing of pull request
        * Run JJB if changing jenkins folder
    * one to run JJB
        * pull request runs this too but the change
        * Afterwards, main build runs and verifies config changes

---

# Demo
