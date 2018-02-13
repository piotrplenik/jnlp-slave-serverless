# Serverless Jenkins JNLP Agent Docker image

[![Docker Stars](https://img.shields.io/docker/stars/pplenik/jnlp-slave-serverless.svg)](https://hub.docker.com/r/pplenik/jnlp-slave-serverless/)
[![Docker Automated build](https://img.shields.io/docker/automated/pplenik/jnlp-slave-serverless.svg)](https://hub.docker.com/r/pplenik/jnlp-slave-serverless/)

This is an image for testing [Serverless](https://serverless.com/) framework for [Jenkins](https://jenkins.io) agent (FKA "slave") using JNLP to establish connection.
This agent is powered by the [Jenkins Remoting library](https://github.com/jenkinsci/remoting), which version is being taken from the base [Docker Agent](https://github.com/jenkinsci/docker-slave/) image.

## Running

To run a Docker container

    docker run pplenik/jnlp-slave-serverless -url http://jenkins-server:port <secret> <agent name>

To run a Docker container with [Work Directory](https://github.com/jenkinsci/remoting/blob/master/docs/workDir.md):

    docker run pplenik/jnlp-slave-serverless -url http://jenkins-server:port -workDir=/home/jenkins/agent <secret> <agent name>

Optional environment variables:

* `JENKINS_URL`: url for the Jenkins server, can be used as a replacement to `-url` option, or to set alternate jenkins URL
* `JENKINS_TUNNEL`: (`HOST:PORT`) connect to this agent host and port instead of Jenkins server, assuming this one do route TCP traffic to Jenkins master. Useful when when Jenkins runs behind a load balancer, reverse proxy, etc.
* `JENKINS_SECRET`: agent secret, if not set as an argument
* `JENKINS_AGENT_NAME`: agent name, if not set as an argument
* `JENKINS_AGENT_WORKDIR`: agent work directory, if not set by optional parameter `-workDir`
