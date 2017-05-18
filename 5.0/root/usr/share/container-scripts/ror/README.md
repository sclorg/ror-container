Ruby on Rails 5.0 platform image
================================

The centos/ror-50-centos7 container image provides a Ruby on Rails 5.0 platform for building and running applications. It contains Ruby 2.4, Ruby on Rails 5.0, and NodeJS 6 preinstalled.


Usgae
-----
The image is to aimed to be used as base image for various layered application images.

To pull the centos/ror-50-centos7 image, run the following command as root:
```
docker pull centos/ror-50-centos7
```

To create a layered container image that uses this image as base, create a Dockerfile as the following:
```
FROM centos/ror-50-centos7
ADD your-app /opt/app-root/src
CMD ...
```

Configuration
-------------

No further configuration is required; this image contains and enables the rh-ruby24, rh-ror50, and rh-nodejs6 Software Collections. For automatic S2I builds, use the Ruby container available as `centos/ruby-24-centos`.
