# MariaDB Dockerfile

## build
    docker build --rm -t linchqd/mariadb:latest .

## run
    
    docker run --name=mariadb -d -p 3306:3306 -v /data/mariadb:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=<password> linchqd/mariadb:latest
    
    可选:
    -e MYSQL_DATABASE=<your database name>
    -e MYSQL_CHARSET=<your database CHARSET>
    -e MYSQL_USER=<your database username>
    -e MYSQL_PASSWORD=<your database password>
    
## more
[MariaDB](https://github.com/CentOS/CentOS-Dockerfiles/tree/master/mariadb/centos7)
