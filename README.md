Ruby on Rails container images
===========================

This repository contains Dockerfiles for Ruby on Rails images.
Users can choose between RHEL and CentOS based images.
For using Ruby on Rails on OpenShift, the preferred variant is
the [Ruby container image](https://github.com/sclorg/s2i-ruby-container),
because this Ruby on Rails image does not support source-to-image strategy.

For more information about contributing, see
[the Contribution Guidelines](https://github.com/sclorg/welcome/blob/master/contribution.md).
For more information about concepts used in these container images, see the
[Landing page](https://github.com/sclorg/welcome).


Versions
---------------
Ruby on Rails versions currently provided are:
* [Ruby on Rails 4.2](4.2)
* [Ruby on Rails 5.0](5.0)

RHEL versions currently supported are:
* RHEL7

CentOS versions currently supported are:
* CentOS7


Installation
----------------------
Choose either the CentOS7 or RHEL7 based image:

*  **RHEL7 based image**

    These images are available in the [Red Hat Container Catalog](https://access.redhat.com/containers/#/registry.access.redhat.com/rhscl/ror-50-rhel7).
    To download it run:

    ```
    $ docker pull registry.access.redhat.com/rhscl/ror-50-rhel7
    ```

    To build a RHEL7 based Ruby on Rails image, you need to run Docker build on a properly
    subscribed RHEL machine.

    ```
    $ git clone --recursive https://github.com/sclorg/ror-container.git
    $ cd ror-container
    $ git submodule update --init
    $ make build TARGET=rhel7 VERSIONS=5.0
    ```

*  **CentOS7 based image**

    This image is available on DockerHub. To download it run:

    ```
    $ docker pull centos/ror-50-centos7
    ```

    To build a CentOS based Ruby on Rails image from scratch, run:

    ```
    $ git clone --recursive https://github.com/sclorg/ror-container.git
    $ cd ror-container
    $ git submodule update --init
    $ make build TARGET=centos7 VERSIONS=5.0
    ```

For using other versions of Ruby on Rails, just replace the `5.0` value by particular version
in the commands above.

**Notice: By omitting the `VERSIONS` parameter, the build/test action will be performed
on all provided versions of Ruby on Rails, which must be specified in  `VERSIONS` variable.
This variable must be set to a list with possible versions (subdirectories).**


Usage
---------------------------------

For information about usage of Dockerfile for Ruby on Rails 4.2,
see [usage documentation](4.2).

For information about usage of Dockerfile for Ruby on Rails 5.0,
see [usage documentation](5.0).

Test
---------------------------------

This repository also provides a test framework, which checks basic functionality
of the Ruby on Rails image.

Users can choose between testing Ruby on Rails based on a RHEL or CentOS image.

*  **RHEL based image**

    To test a RHEL7 based Ruby on Rails image, you need to run the test on a properly
    subscribed RHEL machine.

    ```
    $ cd nginx-container
    $ git submodule update --init
    $ make test TARGET=rhel7 VERSIONS=5.0
    ```

*  **CentOS based image**

    ```
    $ cd nginx-container
    $ git submodule update --init
    $ make test TARGET=centos7 VERSIONS=5.0
    ```

For using other versions of Nginx, just replace the `5.0` value by particular version
in the commands above.

**Notice: By omitting the `VERSIONS` parameter, the build/test action will be performed
on all provided versions of Nginx, which must be specified in  `VERSIONS` variable.
This variable must be set to a list with possible versions (subdirectories).**
