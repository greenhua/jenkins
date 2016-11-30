FROM centos:latest

RUN yum -y install wget sudo

RUN rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
RUN rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
RUN wget http://repo.mysql.com//mysql57-community-release-el7-9.noarch.rpm -O /root//mysql57-community-release-el7-9.noarch.rpm
RUN rpm -i /root//mysql57-community-release-el7-9.noarch.rpm
RUN yum -y update

RUN yum -y install nginx httpd-devel.x86_64  supervisor
RUN yum -y install php70w php70w-opcache  php70w-fpm php70w-opcache
RUN yum -y install mysql-community-server

RUN sed -i -e 's/Defaults    requiretty.*/ #Defaults    requiretty/g' /etc/sudoers
RUN sudo -u mysql /usr/sbin/mysqld --initialize-insecure

COPY etc/supervisord.conf /etc/supervisord.conf

EXPOSE 80

CMD ["/usr/bin/supervisord"]

