FROM centos

MAINTAINER Norikazu Hiraki

# install basic packages
RUN yum install -y wget

# install Jenkins
RUN yum install -y java-1.7.0-openjdk java-1.7.0-openjdk-devel 
RUN wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
RUN rpm --import http://pkg.jenkins-ci.org/redhat/jenkins-ci.org.key
RUN yum install -y jenkins
RUN chkconfig jenkins on

EXPOSE 8080

# start Jenkins
CMD /etc/alternatives/java -Dcom.sun.akuma.Daemon=daemonized -Djava.awt.headless=true -DJENKINS_HOME=/var/lib/jenkins -jar /usr/lib/jenkins/jenkins.war --logfile=/var/log/jenkins/jenkins.log --webroot=/var/cache/jenkins/war --httpPort=8080 --ajp13Port=8009 --debug=5 --handlerCountMax=100 --handlerCountMaxIdle=20
