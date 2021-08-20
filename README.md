# xld-hello-world

This project shows how to use Integration Server Gradle Plugin to run Deploy for testing purposes.
The configuration is the easiest to get the grasp what is the minimum configuration required to make setup up and 
running and as a bonus to see "Deploy Hello World" on a top navigation bar :) 

![Deploy 10.2.2](./pics/deploy-10.2.2.png)

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

if you want to check logs of Deploy:

* run `docker ps` to find the container id 

![Docker PS](./pics/docker-ps.png)

In my example I stopped all other containers, and have only one running, in your case you can have a list, so you have 
to find the one which has the image name "xebialabs/xl-deploy:10.2.2".

* run `docker logs <CONTAINER ID> -f` and you'll see something like that:

![Deploy logs](./pics/deploy-logs.png)

You can pay attention to this message `You can now point your browser to 'http://3595818225d2:4516/'`.
Take into account that the host name in this case shown for the host inside of the container. 
You have to go instead to a http://localhost:4516 as this redirection is configured in Docker compose as we saw it from
`docker ps` in PORTS column.

One of the options how you can shut down the running docker image and unmount all volumes is to run this command:
`./gradlew shutdownIntegrationServer`.
