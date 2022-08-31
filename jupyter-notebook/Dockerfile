#FROM jairamc/spark-kafka-streaming
FROM nopponaim603/spark-streaming-kafka:3.1.2
#FROM jupyter/all-spark-notebook:spark-3.1.2

# Environment
# ENV SPARK_VERSION 3.1.2
# ENV HADOOP_VERSION 2.7
# ENV SCALA_VERSION 2.12

# Fix: https://github.com/hadolint/hadolint/wiki/DL4006
# Fix: https://github.com/koalaman/shellcheck/wiki/SC3014
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

USER root

# Pip
RUN apt-get -y update && \
    apt-get -y install python3-pip && \
    pip3 install --upgrade pip

# Notebook
RUN pip --no-cache-dir install jupyter

# Apache Toree: Scala kernal for the Jupyter Notebook
# https://toree.apache.org/
#RUN cd /tmp && \
#    wget https://dlcdn.apache.org/incubator/toree/0.4.0-incubating/toree/toree-0.4.0-incubating-bin.tar.gz && \
#COPY ./toree-0.2.0.dev1.tar.gz /tmp/
#COPY ./toree-0.4.0.tar.gz /tmp/

#RUN pip --no-cache-dir install /tmp/toree-0.2.0.dev1.tar.gz && \
#    jupyter spylon & toree install
RUN pip install --upgrade toree && \
    jupyter toree install

RUN pip install spylon-kernel

EXPOSE 8888
