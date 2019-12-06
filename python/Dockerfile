FROM linchqd/centos7.6:base

RUN yum -y install wget && cd /etc/yum.repos.d/ && rm -rf ./* \
    && wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo \
    && sed  -i '/aliyuncs/d' /etc/yum.repos.d/CentOS-Base.repo \
    && wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo \
    && sed -i '/aliyuncs/d' /etc/yum.repos.d/epel.repo \
    && yum clean all && yum makecache \
    && yum -y install redhat-lsb-core net-tools vim openssl-devel bzip2-devel expat-devel \
    gdbm-devel readline-devel sqlite-devel gcc unzip libffi-devel lzma zlib-devel openssl-static \
    ncurses-devel readline-devel tk-devel db4-devel libpcap-devel xz-devel \
    && yum clean all && rm -rf /var/cache/yum && rm -rf /var/lib/yum

# ADD https://www.python.org/ftp/python/3.7.3/Python-3.7.3.tgz /usr/local/src/

ADD Python-3.7.3.tgz /usr/local/src/

RUN cd /usr/local/src/Python-3.7.3/ && ./configure --prefix=/usr/local/python3 --enable-optimizations \
    && make && make install && cd / && ln -s /usr/local/python3/bin/* /usr/local/bin/ && rm -rf /usr/local/src/Python-3.7.3/

CMD ["/usr/local/python3/bin/python3"]

