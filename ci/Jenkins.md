# Introduction to Jenkins

## What is Continuous Integration?

* The practice of merging all developer working copies to a shared mainline several times a day.

## Advantages:

* Maintain a code repository.
* Automate the build.
* Make the build self-testing.
* Everyone commits to the baseline every day.
* Keep the build fast.
* Test in a clone of the production environment.
* Make it easy to get the latest deliverables.
* Everyone can see the results of the latest build.
* Automate deployment.
* Integration bugs are detected early and are easy to track down due to small change sets. This saves both time and money over the lifespan of a project.
* Avoids last-minute chaos at release dates, when everyone tries to check in their slightly incompatible versions.
* When unit tests fail or a bug emerges, if developers need to revert the codebase to a bug-free state without debugging, only a small number of changes are lost (because integration happens frequently).
* Constant availability of a "current" build for testing, demo, or release purposes.
* Frequent code check-in pushes developers to create modular, less complex code.

## What is Jenkins?

* A Continuous Integration software.
* Its Web based and Java based tool.
* Can be used as distributed build server.

## Prerequisites

* Java 1.5 (JDK) or higher
* Java in your environment path
* Web server (Only if you want to host outside of Jenkins)

## Install Jenkins on Ubuntu 16.04

* Download Jenkins .war file from [jenkins.io](https://jenkins.io/)
* Extract .war file and Open terminal => go to extracted directory
* Execute below command

```
java -jar jenkins.war
```

Jenkins will start on port 8080 by default. ```--httpPort=<port>``` will help to set different port.

```
java -jar jenkins.war --httpPort=9000
```

Initial admin password file called ```initialAdminPassword``` gets created under ```/home/<username>/.jenkins/secrets/```

Use this password on http://localhost:8080 on browser while setting up Jenkins.

## The build process

1. Check in changes.
2. Get the latest code.
3. Build source.
4. Build tests.
5. Run tests.
6. Report results.

## Build triggers

Build triggers is a thing inside Jenkins that will help us to configure when to trigger source build.

1. After other projects
Run your job after some project finishes.

2. Periodically
Run your job every 5 mins, or a day etc. on specific time frame.

3. Poll source control
Run your job looks in source code control for changes and if there are any changes than build trigger will get fired.

## Refs

* https://en.wikipedia.org/wiki/Continuous_integration
