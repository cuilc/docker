FROM centos:7
MAINTAINER cuilc <feiyu311@qq.com>
LABEL name="CentOS7 java 8, tomcat 7, php, mysql+mycat" \
    vendor="CentOS" \
    license="GPLv2" \
    build-date="20160716"

# Default to UTF-8 file.encoding
ENV LANG C.UTF-8

RUN yum update -y
RUN yum install -y wget
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.rpm

RUN rpm -ivh jdk-8*-linux-x64.rpm && rm jdk-8*-linux-x64.rpm

ENV JAVA_HOME /usr/java/latest
ENV PATH $PATH:$JAVA_HOME/bin

RUN wget http://mirrors.cnnic.cn/apache/tomcat/tomcat-9/v9.0.0.M9/bin/apache-tomcat-9.0.0.M9.tar.gz
RUN tar xf apache-tomcat-9.0.0.M9.tar.gz -C /opt && rm -f apache-tomcat-9.0.0.M9.tar.gz

RUN wget https://raw.githubusercontent.com/MyCATApache/Mycat-download/master/1.5-RELEASE/Mycat-server-1.5.1-RELEASE-20160705210037-linux.tar.gz
RUN tar xf Mycat-server-1.5.1-RELEASE-20160705210037-linux.tar.gz -C /opt && rm -f Mycat-server-1.5.1-RELEASE-20160705210037-linux.tar.gz


EXPOSE 80
EXPOSE 8066
EXPOSE 9066
CMD ["/bin/bash"]
ENTRYPOINT /opt/mycat/bin/mycat start
