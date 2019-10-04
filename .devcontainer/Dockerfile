# FROM Ubuntu Latest LTS
FROM ubuntu:latest

# Disable warnings by switching to non interactive
ENV DEBIAN_FRONTEND=noninteractive

# 2>&1: Redirect stderr to stdout
# Update base image
RUN apt-get update \
  && apt-get -y install --no-install-recommends apt-utils dialog 2>&1

# Install required tools
RUN apt-get -y install \
  git \
  iproute2 \
  curl \
  procps \
  unzip \
  apt-transport-https \
  ca-certificates \
  gnupg-agent \
  software-properties-common \
  lsb-release 2>&1

# Install dependencies for Ansible installation
RUN apt-get install -y libssl-dev libffi-dev python-dev python-pip

RUN pip install ansible

# Cleanup image
RUN apt-get autoremove -y \
  && apt-get clean -y \
  && rm -rf /var/lib/apt/lists/*

ENV DEBIAN_FRONTEND=dialog

RUN mkdir /workspaces
WORKDIR /workspaces