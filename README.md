# Tags
> _Built from [`quay.io/ibm/openjdk:11.0.8`](https://quay.io/repository/ibm/openjdk?tab=info)_
-	`4.3` - [![Build Status](https://travis-ci.com/lcarcaramo/docker-agent.svg?branch=master)](https://travis-ci.com/lcarcaramo/docker-agent)

### __[Original Source Code](https://github.com/jenkinsci/docker-agent)__

Jenkins Agent Docker image
===

This is a base image for Docker, which includes JDK and the Jenkins agent executable (agent.jar).
This executable is an instance of the [Jenkins Remoting library](https://github.com/jenkinsci/remoting).

# How to Use This Image

This image is used as the basis for the [Docker Inbound Agent](https://github.com/jenkinsci/docker-inbound-agent/) image.
In that image, the container is launched externally and attaches to Jenkins.

This image may instead be used to launch an agent using the **Launch method** of **Launch agent via execution of command on the master**. For example on Linux you can try

```sh
docker run -i --rm --name agent --init quay.io/ibm/jenkins-agent:4.3 java -jar /usr/share/jenkins/agent.jar
```

after setting **Remote root directory** to `/home/jenkins/agent`.


## Agent Work Directories

Starting from [Remoting 3.8](https://github.com/jenkinsci/remoting/blob/master/CHANGELOG.md#38) there is a support of Work directories, 
which provides logging by default and change the JAR Caching behavior.

Call example:

```sh
docker run -i --rm --name agent1 --init -v agent1-workdir:/home/jenkins/agent quay.io/ibm/jenkins-agent:4.3 java -jar /usr/share/jenkins/agent.jar -workDir /home/jenkins/agent
```

# License

MIT License: See details [here](https://github.com/jenkinsci/docker-agent/blob/master/LICENSE).
