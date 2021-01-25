FROM opensuse/leap:15.1
LABEL maintainer="Tinashe Chikomo <tinashe@chikomo.net>"

ENV container docker

RUN zypper -n install systemd; zypper clean ; \
(cd /usr/lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /usr/lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /usr/lib/systemd/system/local-fs.target.wants/*; \
rm -f /usr/lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /usr/lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /usr/lib/systemd/system/basic.target.wants/*;\
rm -f /usr/lib/systemd/system/anaconda.target.wants/*;

# Install ansible
RUN zypper -n install git ansible sudo python2-pip python3-pip openssh curl tar unzip gzip rsync; zypper clean

# Upgrade pip
RUN python3 -m pip install --upgrade pip

# Install Ansible pip package
RUN python3 -m pip install ansible

VOLUME [ "/sys/fs/cgroup" ]

ENTRYPOINT ["/usr/lib/systemd/systemd", "--system"]