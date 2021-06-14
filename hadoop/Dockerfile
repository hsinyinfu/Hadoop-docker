FROM ubuntu:20.04
LABEL maintainer="Hsin-Yin Fu"
LABEL maintainer_email="peter0930260535@gmail.com"

RUN useradd --create-home --shell /bin/bash --groups sudo hadoop
RUN /bin/echo -e 'hadoop\nhadoop' | passwd hadoop
RUN apt-get update && apt-get install -y curl ssh openjdk-11-jdk vim && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64" HADOOP_HOME="/usr/local/hadoop"
EXPOSE 9870/TCP 9868/TCP 9864/TCP 8088/TCP

RUN curl -o hadoop.tar.gz https://downloads.apache.org/hadoop/common/hadoop-3.3.0/hadoop-3.3.0.tar.gz \
	&& tar xzvf hadoop.tar.gz -C /usr/local \
	&& rm hadoop.tar.gz \
	&& mv /usr/local/hadoop-3.3.0 /usr/local/hadoop \
	&& chown -R hadoop:hadoop /usr/local/hadoop

USER hadoop
WORKDIR /usr/local/hadoop
