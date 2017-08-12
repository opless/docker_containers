FROM ubuntu:16.04
MAINTAINER Simon Waite <opless@gmail.com>
#########################################################################
# Simon Waite                              Sat 12 Aug 2017 09:20:51 BST #
# opless@gmail.com                                                      #
#########################################################################
#
# Stub Dockerfile for creating Dockerfiles with ansible
# 
# Ideas borrowed from https://github.com/philm/ansible_playbook
#
#
#########################################################################

ENV HOME /root
ENV DEBIAN_FRONTEND noninteractive

# Enusure we're update, have a minimal dev environment,
# Then get rid of apt.
# Then get pip, as ubuntus version has been fiddled with.
# Install latest ansible and set things up for localhost.

RUN apt-get update && \
    apt-get install -y --force-yes build-essential cmake git pkg-config \
                python2-dev wget curl && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* \
           /tmp/* \
           /var/tmp/* && \
    mkdir ~/tmp && cd ~/tmp && \
    wget -O get-pip.py https://bootstrap.pypa.io/get-pip.py && \
    python get-pip.py && \
    cd .. && \
    rm -rf tmp && \
    pip install ansible && \
    mkdir /etc/ansible/ /ansible && \
    echo "[local]" >> /etc/ansible/hosts && \
    echo "localhost" >> /etc/ansible/hosts && \
    mkdir -p /work 

WORKDIR /work

ENV ANSIBLE_GATHERING smart
ENV ANSIBLE_HOST_KEY_CHECKING false
ENV ANSIBLE_RETRY_FILES_ENABLED false
ENV ANSIBLE_ROLES_PATH /ansible/playbooks/roles
ENV ANSIBLE_SSH_PIPELINING True
