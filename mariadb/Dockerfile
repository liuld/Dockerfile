FROM linchqd/centos7.6:base

RUN yum -y install wget && \
    cd /etc/yum.repos.d/ && \
    rm -rf ./* && \
    wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo && \
    sed  -i '/aliyuncs/d' /etc/yum.repos.d/CentOS-Base.repo && \
    wget -O /etc/yum.repos.d/epel.repo http://mirrors.aliyun.com/repo/epel-7.repo && \
    sed -i '/aliyuncs/d' /etc/yum.repos.d/epel.repo && \
    yum -y install --setopt=tsflags=nodocs epel-release && \
    yum -y install --setopt=tsflags=nodocs mariadb-server bind-utils pwgen psmisc hostname && \
    yum -y erase vim-minimal && \
    yum -y update && yum clean all && \
    rm -rf /var/cache/yum && \
    rm -rf /var/lib/yum

# Fix permissions to allow for running on openshift
COPY fix-permissions.sh ./
RUN ./fix-permissions.sh /var/lib/mysql/   && \
    ./fix-permissions.sh /var/log/mariadb/ && \
    ./fix-permissions.sh /var/run/

COPY docker-entrypoint.sh /

ENTRYPOINT ["/docker-entrypoint.sh"]

VOLUME /var/lib/mysql

USER 27

EXPOSE 3306
CMD ["mysqld_safe"]
