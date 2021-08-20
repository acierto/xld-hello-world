# xld-hello-world

This project shows how to use Integration Server Gradle Plugin to run Deploy for testing purposes.
The configuration is the easiest to get the grasp what is the minimum configuration required to make setup up and 
running and as a bonus to see "Deploy Hello World" on a top navigation bar :) 

The configuration how to run Gradle task, can be found in `.gradle/workflows/build.yaml`.
If you are going to configure it on a bare metal, you have to be sure you next the things installed:

* Java 11
* Docker
* Docker Compose 

Deploy will be running in a docker container and by these properties you can configure from which repository to 
pull it from and which version to use:

```groovy
dockerImage = "xebialabs/xl-deploy"
version = "10.2.2"
```

The server label, which is displayed on a top navigation bar is possible to configure in `deploy-server.yaml` which
is a part of central configuration.

The official documentation:
https://docs.xebialabs.com/xl-deploy/10.2.x/javadoc/deploy-configuration-api/properties-api/index.html#deployserver-deploy-serveryaml

 
