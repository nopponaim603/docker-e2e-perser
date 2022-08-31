FROM ubuntu

# Environment
ENV SPARK_VERSION 3.1.2
ENV HADOOP_VERSION 2.7
ENV SCALA_VERSION 2.12
ENV SPARK_HOME /usr/local/spark
ENV HADOOP_HOME /usr/local/spark
# wget
RUN apt-get -y update && apt-get install -y wget

# Java
RUN apt-get install -y --no-install-recommends openjdk-8-jre-headless

# Hadoop
# https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz
# RUN cd /tmp && \
#    wget https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz && \
#    tar -xvzf https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz -C /usr/local && \
#    rm https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz

#RUN cd /usr/local && ln -s https://dlcdn.apache.org/hadoop/common/hadoop-3.3.4/hadoop-3.3.4.tar.gz hadoop

# Spark
# Old version
# http://d3kbcqa49mib13.cloudfront.net/spark-2.2.0-bin-hadoop2.6.tgz

# achive version
# https://archive.apache.org/dist/spark/spark-2.2.0/spark-2.2.0-bin-hadoop2.7.tgz

# stable version
# https://dlcdn.apache.org/spark/spark-3.1.3/spark-3.1.3-bin-hadoop2.7.tgz
# lasted not compatible
# https://dlcdn.apache.org/spark/spark-3.3.0/spark-3.3.0-bin-hadoop3-scala2.13.tgz

RUN cd /tmp && \
    wget https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && \
    tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz -C /usr/local && \
    rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz

RUN cd /usr/local && ln -s spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark

# Spark Kafka Streaming
# Older
# wget http://repo1.maven.org/maven2/org/apache/spark/spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}/${SPARK_VERSION}/spark-streaming-kafka-0-10-assembly_${SCALA_VERSION}-${SPARK_VERSION}.jar && \
# Current Version
# https://repo1.maven.org/maven2/org/apache/spark/spark-streaming-kafka-0-10_2.12/3.1.3/spark-streaming-kafka-0-10_2.12-3.1.3.jar
RUN cd /tmp && \
    wget https://repo1.maven.org/maven2/org/apache/spark/spark-streaming-kafka-0-10_${SCALA_VERSION}/${SPARK_VERSION}/spark-streaming-kafka-0-10_${SCALA_VERSION}-${SPARK_VERSION}.jar && \
    mv spark-streaming-kafka-0-10_${SCALA_VERSION}-${SPARK_VERSION}.jar /usr/local/spark/jars

# Spark Kafka sql
# https://repo1.maven.org/maven2/org/apache/spark/spark-sql-kafka-0-10_2.12/3.1.3/spark-sql-kafka-0-10_2.12-3.1.3.jar

RUN cd /tmp && \
    wget https://repo1.maven.org/maven2/org/apache/spark/spark-sql-kafka-0-10_${SCALA_VERSION}/${SPARK_VERSION}/spark-sql-kafka-0-10_${SCALA_VERSION}-${SPARK_VERSION}.jar && \
    mv spark-sql-kafka-0-10_${SCALA_VERSION}-${SPARK_VERSION}.jar /usr/local/spark/jars

# Spark token provider kafka
# https://repo1.maven.org/maven2/org/apache/spark/spark-token-provider-kafka-0-10_2.12/3.1.3/spark-token-provider-kafka-0-10_2.12-3.1.3.jar

RUN cd /tmp && \
    wget https://repo1.maven.org/maven2/org/apache/spark/spark-token-provider-kafka-0-10_${SCALA_VERSION}/${SPARK_VERSION}/spark-token-provider-kafka-0-10_${SCALA_VERSION}-${SPARK_VERSION}.jar && \
    mv spark-token-provider-kafka-0-10_${SCALA_VERSION}-${SPARK_VERSION}.jar /usr/local/spark/jars

EXPOSE 8080

EXPOSE 6066

EXPOSE 7077
