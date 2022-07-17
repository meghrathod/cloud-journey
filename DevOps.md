# 1. Intro to DevOps
![[Lifecycleof DevOps.png]]

## Steps in DevOps:
DevOps was originally envisioned as a way to structure engineering organizations to efficiently integrate user feedback:

1.  A plan is made for what users might need, often in scrum meetings between product managers and developers.
2.  Developers write code based on what was planned.
3.  The code is built into artifacts (containers, apps, executables, etc.)
4.  Those artifacts are tested automatically and/or by QA teams.
5.  Once the artifacts are confirmed to be error free by testing and QA, they are combined into a release (version 2.0.0, for example)
6.  That release is distributed (the file is hosted, the containers are deployed, the apps are published, etc)
7.  After the release is distributed, the application need to be monitored for code errors and scaling problems.
8.  Monitoring keeps track of key metrics: Does the product feel slow, is it down?

## The three pillars of DevOps Engineering

### Pull request automation
-   Automated test running with a CI provider ([what is CI?](https://webapp.io/blog/what-is-ci/)), which gives developers confidence that the change does not break existing functionality
-   Per-change ephemeral environments, which helps interested parties actually interact with the proposed change to ensure it solves all required business goals.
-   Automated security scanning, which helps ensure that proposed changes do not introduce new vulnerabilities into the product.
-   Notifications to reviewers automatically, so that the correct reviewers can quickly request changes to a pull request.

### Deployment automation
-   Deploying a feature to a certain set of users as a final test before rolling it out more publicly (feature flagging and canary deployments)
-   Starting new versions of services without causing downtime (blue/green deployments and rolling deployments)
-   Rolling back to the prior version in case something does go wrong.

### Application performance management
1.  **Metrics**: Numerical measurements of key numbers in production.
2.  **Logging:** Text descriptions of what is happening during processing.
3.  **Monitoring:** Take the metrics and logs and convert them into health metrics
4.  **Alerting:** If monitoring detects a problem, the correct problem-solver should be notified automatically

## Examples of DevOps Engineering:
1. new startup with no users and building a new application
	* GitHub, Netlify, LayerCI
2. Team with 10+ enterprise customers
	* Github, Sentry(Automated log collection), CodeCov(Automated Test Running), Bitrise(mobile testing and alerting), Pedro duty(who should be notified in case of an issue)
3. Large Organisation: Github Enterprise(or custom version control solutions), Sentry, ElasticSearch/LogStash/Kibana(for looking at logs), pingdom(check pages), launch darkly(show limited features to limited users), terraform(automatically create plans)

> Conclusion: Vital for engineering teams and especially as product matures

# 2. What is TDD

> TDD or Test Driven Development Definition: coding methodology where tests are written before code with developed

Unit test: each component works
Integration test: few components work together
End-to-End test: All the components works together
Acceptance test: Check after release if it is working

## Flow without TDD:
1. Choose work
2. Build it based of specs
3. Test it with small scripts

## Flow with TDD
1. Choose something to work on
2. Write tests for specs 
3. Build till the tests are passes

# 3. CI
> Continuous Integration means that the code that is pushed to repositories per day are verified by automativ software that runs comprehensive tests to ensure no major issues are seen by customers.

## 3.1 Benefits of CI
* CI is the first step to DevOps automation and helps with code collaboration
> after some time a critical bug is found! So he needs to make changes, so he needs CI
* CI improve dev speed without breaking code
* CI prevents broken code from creeping in

## 3.2 Branch based
* Have a main branch that is availabe to users
* Then create branches of features from the working branch and add features
* Once it clears CI and QA merge(using pull requests) it with the main branch
* ![[CI using Branching.png]]
* Example include: Github Actions

> CI is vital tool, easy to implement and must for developers as it increases collaboration, prevents error and increases user satisfaction


