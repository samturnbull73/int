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
