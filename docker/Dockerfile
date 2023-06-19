
FROM    ubuntu:22.04

SHELL   ["/bin/bash", "-c"]
ARG     DEBIAN_FRONTEND noninteractive

# Install software packages
RUN     apt-get update && \
        apt-get install -y --no-install-recommends \
          curl \
          default-jre \
          less \
          tree \
          unzip \
          vim \
          wget \
          zip \
          ;

# download transform package
WORKDIR /usr/src/pds-transform
RUN     wget https://github.com/NASA-PDS/transform/releases/download/v1.11.5/transform-1.11.5-bin.zip

# install transform package
WORKDIR /usr/local/
RUN     unzip /usr/src/pds-transform/transform-1.11.5-bin.zip 

# configure environment
ENV     PATH ${PATH}:/usr/local/transform-1.11.5/bin
ENV     JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64

# Default container setup
CMD     ["/bin/bash"]
COPY    Dockerfile /




