Ruby on Rails 4.2 platform Docker image
================================

This container image includes Ruby on Rails 4.2 platform for general usage.
Users can choose between RHEL and CentOS based images.
The RHEL image is available in the [Red Hat Container Catalog](https://access.redhat.com/containers/#/registry.access.redhat.com/rhscl/ror-42-rhel7)
as registry.access.redhat.com/rhscl/ror-42-rhel7.
The CentOS image is then available on [Docker Hub](https://hub.docker.com/r/centos/ror-42-centos7/)
as centos/ror-42-centos7.


Description
-----------

Ruby on Rails is a full-stack web framework optimized for programmer happiness 
and sustainable productivity. It encourages beautiful code by favoring convention over configuration. 
The container image provides a Ruby on Rails 4.2 platform for building and running applications. 
It contains Ruby 2.3, Ruby on Rails 4.2, and NodeJS 4 preinstalled.


Usage
-----
The image is to aimed to be used as base image for various layered application images.

To pull the rhscl/ror-42-rhel7 image, run the following command as root:
```
docker pull rhscl/ror-42-rhel7
```

To create a layered container image that uses this image as base, create a Dockerfile as the following:
```
FROM rhscl/ror-42-rhel7
COPY your-app /opt/app-root/src
CMD ...
```


Configuration
-------------

No further configuration is required.
This image contains and enables the rh-ruby23, rh-ror42, and rh-nodejs4 Software Collections.


S2I build support
-------------
This image doesn't support S2I tool.
For automatic S2I builds, use the Ruby container available as `rhscl/ruby-23-rhel7` for RHEL or `centos/ruby-23-centos7` for CentOS.

Environment variables and volumes
-------------
No special environment variables or volumes available.

Troubleshooting
---------------
Container log can be examined by running:

    docker logs <container>


See also
--------
Dockerfile and other sources for this container image are available on
https://github.com/sclorg/ror-container.
In that repository, Dockerfile for CentOS is called Dockerfile, Dockerfile
for RHEL is called Dockerfile.rhel7.
