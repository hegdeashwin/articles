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

## Prerequisites

* Java 1.5 (JDK) or higher
* Java in your environment path
* Web server (Only if you want to host outside of Jenkins)

## Install Jenkins

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

## Refs

* https://en.wikipedia.org/wiki/Continuous_integration
