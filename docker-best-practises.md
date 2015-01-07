# Docker Best Practises

- Use Ubuntu trusty if possible (FROM ubuntu:trusty)
- Add Dell Cloud Market Place as maintainer for each image (MAINTAINER Dell Cloud Market Place <Cloud_Marketplace@dell.com>)
- Base images should always detail the repository and the specific tag the image is based on.
```
FROM dell/lamp:1.0
```
- Don’t do RUN apt-get update on a single line. This will cause caching issues if the referenced archive gets updated, which will make your subsequent apt-get install fail without comment.
- Avoid RUN apt-get upgrade or dist-upgrade, since many of the “essential” packages from the base images will fail to upgrade inside an unprivileged container.
- Put long or complex RUN statements on multiple lines separated with backslashes. (Ex: apt-get update )
- The RUN instruction, try to combine commands that are part of one cohesive operation. The one RUN instruction will mean only one layer gets used.
```
RUN apt-get update && apt-get install -yq \
   build-essential \ 
   libcurl4-openssl-dev \
   libreadline-dev \
   libssl-dev \
   libyaml-dev \
   libxml2-dev \
   python-software-properties \
   zlib1g-dev
```

- Lines should not exceed 80 characters 
- Expose the common, traditional ports used by the application
- Try to put the commands likely to change at the end of the docker file
- Comments format: # This a comment
- Skip a line between 2 blocks of commands
- Use supervisor if the application/process may need to be restarted from the container (eg, HTTP Server)
- Use ENTRYPOINT to use a helper/startup script
- VOLUME should be used to expose any database storage area, configuration storage, or files/folders created by the docker container
- Backup the folders used as exposed volumes and copy the content back in the startup script
- Always use absolute paths for your WORKDIR
- Use WORKDIR instead of proliferating instructions like RUN cd … && do-something, which are hard to read, troubleshoot, and maintain
- Expose variables likely to be set by the user of the container
