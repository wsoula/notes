Prerequisite:
---
# sudo apt-get update
# sudo apt-get install openjdk-7-jdk
# wget http://mirrors.jenkins-ci.org/war/latest/jenkins.war
# screen -S jenkins
# sudo java -jar jenkins.war --httpPort=80
# ctrl A + D
# sudo apt-get install git
# ssh-keygen and add to github

Steps
---
# git clone git@github:openstack-infra/jenkins-job-builder
# cd jenkins-job-builder
# wget https://bitbucket.org/pypa/setuptools/raw/bootstrap/ez_setup.py -O - | sudo python
# sudo apt-get install python-pip
# pip install pbr
# sudo python setup.py install
# sudo mkdir /etc/jenkins_jobs
# sudo vi /etc/jenkins_jobs/jenkins_jobs.ini
# create jjb-init yaml
# jenkins-job update jjb-init.yaml
# add git, ghprb, embeddable build status plugins
# add credentials for root user

---

# Demo

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
