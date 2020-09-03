[Docker](https://github.com/samturnbull73/int/blob/master/NOTES.md#docker)


### Docker

| Tag           | Description | Example |
| ------------- | ------------- |----|
| MAINTAINER  | who is maintaining this Dockerfile  | |
| FROM | tell who is maintaining this Dockerfile | |
| CMD |  The command executed when running a Docker container based on this image |  | 
| COPY | install software and copy files into the image. | |
| ADD | same way as the COPY instruction, tar or pull file from over http/s  | |
| ENV |  set an environment variable inside the Docker image  | |
| RUN | execute command line executables, executed during build time, exe once | |
| ARG | lets you define an argument which can be passed to Docker when you build the Docker image | ARG tcpPort=8080 |
| WORKDIR | specifies what the working directory should be inside the Docker image | |
| EXPOSE | opens up network ports in the Docker container to the outside world | EXPOSE   8080/tcp 9999/udp |
| VOLUME | creates a directory inside the Docker image which you can later mount a volume (directory) to from the Docker host  | VOLUME   /data|
| ENTRYPOINT | application or command that is executed when the Docker container is started up | |
| HEALTHCHECK | health check interval --interval=60s, Health Check Start Period --start-period=300s, Health Check Retries --retries=5| |

### CI and CD

CI when a developer checks in his code into git, with the help of git-hook, a build will be triggered in Jenkins, which will test for build
we do unit testing like jmeter(they had their own custom unit testing tool) 

In CD- we do build, static code analysis using Sonarcube, deploy the artefact to Artificatory and do Functional testing using Selenium

If it passes the test, we deploy the code to next environment from Artifactory as do further testing

We do performance testing in Preprod environment

For performance testing, you may use tools like Appdynamics, New Relic, we were using load runner.
