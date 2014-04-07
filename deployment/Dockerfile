# DOCKER-VERSION 0.3.4
FROM    ubuntu:latest

# Author
MAINTAINER Jarl Stefansson <jarl@sdelements.com>

# Add 10gen official apt source to the sources list
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
RUN echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' | tee /etc/apt/sources.list.d/10gen.list

# Hack for initctl not being available in Ubuntu
#RUN dpkg-divert --local --rename --add /sbin/initctl
#RUN ln -s /bin/true /sbin/initctl

#Update apt
RUN apt-get update

# Install MongoDB
RUN apt-get install -y mongodb-10gen

# Create the MongoDB data directory
RUN mkdir -p /data/db

# Add node repos
RUN apt-get install -y software-properties-common
RUN apt-get install -y software-properties-common python-software-properties
RUN add-apt-repository -y ppa:chris-lea/node.js

# Update apt
RUN apt-get update

# Install Node
RUN apt-get install -y nodejs

# Expose port
EXPOSE 27017
ENTRYPOINT ["usr/bin/mongod"]

# Enable EPEL for Node.js
#RUN     rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

# Install Node.js and npm
#RUN     yum install -y npm

# Bundle app source
ADD ../ /docs

# Install app dependencies
RUN cd /src; npm install

EXPOSE  80 443
CMD ["node", "/docs/app.js"]
