FROM centos:centos7

ENV SUMMARY="Platform for building and running Ruby on Rails 4.1 applications" \
    DESCRIPTION="Ruby on Rails is a full-stack web framework optimized for programmer happiness \
and sustainable productivity. It encourages beautiful code by favoring convention over configuration. \
The container image provides a Ruby on Rails 4.1 platform for building and running applications. \
It contains Ruby 2.2, Ruby on Rails 4.1, and NodeJS 0.10 preinstalled."

LABEL summary="$SUMMARY" \
      description="$DESCRIPTION" \
      io.k8s.description="$SUMMARY" \
      io.k8s.display-name="Ruby on Rails 4.1" \
      com.redhat.component="rh-ror41-docker" \
      name="centos/ror-41-centos7" \
      version="4.1" \
      release="1"

# The following is taken from STI base image so this Dockerfile follows the same convetions.
# https://github.com/openshift/sti-base/blob/master/Dockerfile

ENV HOME=/opt/app-root/src \
    PATH=/opt/app-root/src/bin:/opt/app-root/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

ENV BASH_ENV=/opt/app-root/etc/scl_enable \
    ENV=/opt/app-root/etc/scl_enable \
    PROMPT_COMMAND=". /opt/app-root/etc/scl_enable"

# Let's install the same as STI images
RUN INSTALL_PKGS="autoconf \
  automake \
  findutils \
  gcc-c++ \
  gdb \
  gettext \
  git \
  libcurl-devel \
  libxml2-devel \
  libxslt-devel \
  lsof \
  make \
  mariadb-devel \
  mariadb-libs \
  openssl-devel \
  patch \
  postgresql-devel \
  procps-ng \
  scl-utils \
  sqlite-devel \
  tar \
  unzip \
  wget \
  which \
  yum-utils \
  zlib-devel" && \
  yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
  rpm -V $INSTALL_PKGS && \
  yum clean all -y && \
  mkdir -p ${HOME} && \
  groupadd -r default -f -g 1001 && \
  useradd -u 1001 -r -g default -d ${HOME} -s /sbin/nologin \
      -c "Default Application User" default && \
  chown -R 1001:1001 /opt/app-root


# This image provides a Ruby on Rails 4.1 environment you can use to run your Rails
# applications.

EXPOSE 8080

ENV RAILS_VERSION 4.1

RUN yum install -y yum-utils && \
    yum install -y centos-release-scl-rh && \
    INSTALL_PKGS="rh-ruby22 rh-ruby22-ruby-devel rh-ruby22-rubygem-rake v8314 rh-ruby22-rubygem-bundler rh-ror41 nodejs010" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

# Install the files that we need in the container
COPY root /

RUN chown -R 1001:1001 /opt/app-root

USER 1001

WORKDIR ${HOME}

# Set the default CMD to print the usage of the language image
ENTRYPOINT ["container-entrypoint"]
CMD ["usage"]
