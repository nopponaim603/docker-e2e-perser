FROM debian:jessie
MAINTAINER Alex Wilson a.wilson@alumni.warwick.ac.uk

# Environment
ENV JAVA_HOME /opt/java
ENV PATH /usr/local/flume/bin:/opt/java/bin:$PATH
ENV DEBIAN_FRONTEND noninteractive
ENV FLUME_VERSION 1.9.0

# wget
RUN apt-get -y update && apt-get install -y wget

# Java
RUN mkdir /opt/java \
    && wget --no-check-certificate --header "Cookie: oraclelicense=accept-securebackup-cookie" -qO- \
          http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.tar.gz \
          | tar zxvf - -C /opt/java --strip 1

#RUN apt-get install -y --no-install-recommends openjdk-8-jre-headless

# Flume
RUN cd /tmp && \
    wget http://archive.apache.org/dist/flume/${FLUME_VERSION}/apache-flume-${FLUME_VERSION}-bin.tar.gz && \
    tar -xvzf apache-flume-${FLUME_VERSION}-bin.tar.gz -C /usr/local && \
    rm apache-flume-${FLUME_VERSION}-bin.tar.gz

RUN cd /usr/local && ln -s apache-flume-${FLUME_VERSION}-bin flume

ADD start-flume.sh /usr/local/flume/bin/start-flume
ADD ./conf/flume.conf /usr/local/flume/conf/flume.conf
ADD ./conf/flume-a1.conf /usr/local/flume/conf/flume-a1.conf
ADD ./conf/flume-a2.conf /usr/local/flume/conf/flume-a2.conf
ADD ./conf/flume-a3.conf /usr/local/flume/conf/flume-a3.conf
ADD ./conf/flume-a4.conf /usr/local/flume/conf/flume-a4.conf
ADD ./conf/flume-a5.conf /usr/local/flume/conf/flume-a5.conf

#ENTRYPOINT [ "start-flume" ]
CMD flume-ng agent -n docker1 -c /usr/local/flume/conf -f /usr/local/flume/conf/flume-a1.conf -Dflumonf/flume-a1.conf -Dflume.root.logger=INFO,console
#CMD flume-ng agent -n docker2 -c /usr/local/flume/conf -f /usr/local/flume/conf/flume-a2.conf -Dflumonf/flume-a2.conf -Dflume.root.logger=INFO,console
#CMD flume-ng agent -n docker3 -c /usr/local/flume/conf -f /usr/local/flume/conf/flume-a3.conf -Dflumonf/flume-a3.conf -Dflume.root.logger=INFO,console
#CMD flume-ng agent -n docker4 -c /usr/local/flume/conf -f /usr/local/flume/conf/flume-a4.conf -Dflumonf/flume-a4.conf -Dflume.root.logger=INFO,console