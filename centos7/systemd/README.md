# Example
    # httpd server dockerfile
        FROM linchqd/centos7.6:systemd
        RUN yum -y install httpd; yum clean all; systemctl enable httpd.service
        EXPOSE 80
        CMD ["/usr/sbin/init"]
    # build
        docker build --rm -t linchqd/centos-httpd:latest .
    # run
        docker run --privileged=true -dit -v /sys/fs/cgroup:/sys/fs/cgroup:ro -p 80:80 linchqd/centos-httpd:latest   
