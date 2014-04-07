# DOCKER-VERSION 0.3.4
FROM    centos:6.4

# Author
MAINTAINER Jarl Stefansson <jarl@sdelements.com>

# Enable EPEL for Node.js
RUN     rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm

# Install Node.js and npm
RUN     yum install -y npm

# Bundle app source
ADD ../ /docs

# Install app dependencies
RUN cd /src; npm install

EXPOSE  80 443
CMD ["node", "/docs/app.js"]
