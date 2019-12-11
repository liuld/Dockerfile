FROM centos:centos7

RUN yum -y install --setopt=tsflags=nodocs epel-release && \
    yum -y install wget nginx redhat-lsb-core net-tools vim openssl-devel bzip2-devel expat-devel \
    gdbm-devel readline-devel sqlite-devel gcc unzip libffi-devel lzma zlib-devel openssl-static \
    ncurses-devel readline-devel tk-devel db4-devel libpcap-devel xz-devel && \
    yum clean all

RUN cd /usr/local/src/ && \
    wget https://npm.taobao.org/mirrors/python/3.7.5/Python-3.7.5.tgz && \
    tar zxvf Python-3.7.5.tgz && \
    cd Python-3.7.5 && \
    ./configure --prefix=/usr/local/python3 --enable-optimizations && \
    make && \
    make install && \
    cd / && \
    ln -s /usr/local/python3/bin/* /usr/local/bin/ && \
    rm -rf Python-3.7.5 Python-3.7.5.tgz

CMD ["/usr/local/bin/python3"]

