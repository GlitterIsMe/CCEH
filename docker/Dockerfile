FROM centos:centos8.3.2011
RUN yum install -y automake autoconf libtool make gcc gcc-c++ gdb cmake gdb-gdbserver&& \
    yum install -y libpmem libpmem-devel libpmemobj libpmemobj-devel libvmem && \
    yum install -y openssl openssh-server rsync&& \
    #sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config && \
    #cmake --version && \
    #g++ -v && \
    echo 'root:123456' | chpasswd && \
    mkdir /var/run/sshd && \
    mkdir /tmp/clion
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N "" && \
    ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N "" && \
    ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N ""
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]