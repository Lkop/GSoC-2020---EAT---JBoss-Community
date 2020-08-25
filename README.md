GSoC submission 2020
===================

### GSoC-2020---EAT---JBoss-Community

Link to the workshop: [EAT_workshop ](https://www.dropbox.com/s/bebhyd1iz7cg1i2/EAT_WORKSHOP.odt?dl=0)

Link to project proposal: [EAT_CI](https://summerofcode.withgoogle.com/projects/#4649931278647296)

----------

Introduction
-------------

Our project, which is included in the category of Software Testing, is related to EAT (EAP Additional Testsuite) with which we can test infinite software project versions. 


#### The advantages of EAT are :

1. Writing the tests once and testing against infinite number of Application Servers.
2. Having all the tests at one place.
3. Comparison of the servers based on the testsuite.
4. Guarding against regression.
5. Faster convergence among the servers.
6. Comparison of the servers based on tests of the past and the present.
7. Addition of tests with possible future features that are not at the moment available.
8. It makes possible to push a testcase of a fix regarding a specific component of the server, without the component version to have been updated at the server pom.
9. Ability to merge tests from remote testsuites.


#### This GSoC 2020 Project had three goals :

1. Expanding the EAT workshop lab ([EAT_workshop](https://www.dropbox.com/s/bebhyd1iz7cg1i2/EAT_WORKSHOP.odt?dl=0)) and adding the latest release of Wildfly (at the time) in EAT.
2. Developing a new autonomous CI (Continuous Integration) tool that combines proposed changes on the server with the equivalent proposed changes or addition on EAT.
3. Making the new CI tool more flexible by generalizing the CI scripts for any AT structure.


GSoC 2020 RESULT / PRODUCTION
------------------------------

#### Phase 1

During the 1st phase I went through the workshop lab. 

Among the tasks was downloading and building the sources of different JBoss servers and JBoss server versions such as [Wildfly](https://github.com/wildfly/wildfly), [Wildfly 20.0.0](https://github.com/wildfly/wildfly/releases/tag/20.0.0.Final) and testing them using [EAT](https://github.com/EAT-JBCOMMUNITY/EAT)

During this phase I have added the latest release (at the time) of Wildfly server in EAT, creating a new test set, which was used with the EAT Travis CI build on Github.  Here is the PR that was merged : [EAT PR 1](https://github.com/EAT-JBCOMMUNITY/EAT/pull/4), [EAT PR 2](https://github.com/EAT-JBCOMMUNITY/EAT/pull/11), [EAT PR 3](https://github.com/EAT-JBCOMMUNITY/EAT/pull/15) and here is the latest successful [Travis CI build](https://travis-ci.com/github/EAT-JBCOMMUNITY/EAT/builds/172926562).

This work was tracked by the following Jira: [GSoC-2020 : Adding latest Wildfly Release 20.0.0.Final in EAT](https://issues.redhat.com/browse/WFLY-13621)

Also, during this phase, I documented the 4th structure ([DependencyTreeParser](https://github.com/EAT-JBCOMMUNITY/EAT/tree/master/DependencyTreeParser)).



#### Phase 2

During this phase, I started developing a basic CI script in bash that sends the results to Github.

*Commits*
- [Creating a CI (script) tool](https://github.com/EAT-JBCOMMUNITY/EAT/pull/30)
- [CI fixes and README](https://github.com/EAT-JBCOMMUNITY/EAT/pull/35)



#### Phase 3

During the 3rd phase, I have continued the CI making it more user friendly by changing its architecture spliting it in files and made it applicable on every combination of software under the AT structure.

Also, I made some improvements and optimizations in order to save excecution time and API requests to Github (limit: 60, 5000 connected)

*Commits*
- [Changing CI's architecture](https://github.com/EAT-JBCOMMUNITY/EAT/pull/40)
- [Adding -all comment option](https://github.com/EAT-JBCOMMUNITY/EAT/pull/42)
- [General form -all and corrections](https://github.com/EAT-JBCOMMUNITY/EAT/pull/43)
- [Minor fixes and optimizations](https://github.com/EAT-JBCOMMUNITY/EAT/pull/50)

Here are the URLs of the project:
- [CI](https://github.com/EAT-JBCOMMUNITY/EAT/tree/master/CI)

The documentation can be found in the README<span></span>.md file inside CI's folder.

*HOW TO BE USED*
The CI scripts could be used from the users in order to test their commits with EAT or inside containers on servers in order form an EAT - CI architecture.
