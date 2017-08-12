FROM opensuse:42.3
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

# Enusure we're update, have a minimal dev environment,
# Then get rid of apt.
# Then get pip, as ubuntus version has been fiddled with.
# Install latest ansible and set things up for localhost.

RUN zypper -n install -t pattern devel_C_C++  && \
    zypper -n install python python-pip python-devel && \
    zypper -n install wget curl git  && \
    pip install --upgrade pip  && \
    pip install ansible  && \
    mkdir /etc/ansible/ /ansible  && \
    echo "[local]" >> /etc/ansible/hosts  && \
    echo "localhost" >> /etc/ansible/hosts  && \
    mkdir -p /work  

WORKDIR /work

ENV ANSIBLE_GATHERING smart
ENV ANSIBLE_HOST_KEY_CHECKING false
ENV ANSIBLE_RETRY_FILES_ENABLED false
ENV ANSIBLE_ROLES_PATH /ansible/playbooks/roles
ENV ANSIBLE_SSH_PIPELINING True
