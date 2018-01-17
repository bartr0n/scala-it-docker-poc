# Spark-1.5.2 docker imagefor RHEL/CentOS 7.x 
FROM centos:centos7

RUN yum install -y java-1.8.0-openjdk
RUN yum clean all && rm -rf /tmp/* /var/tmp/* /var/cache/yum/*

# Download and extract spark
#RUN curl -s http://d3kbcqa49mib13.cloudfront.net/spark-1.5.2-bin-hadoop2.4.tgz | tar -xz -C /tmp
#RUN mv /tmp/spark-1.5.2-bin-hadoop2.4 /usr/lib/spark
#ENV SPARK_HOME="/usr/lib/spark"

RUN curl -s http://d3kbcqa49mib13.cloudfront.net/spark-1.6.1-bin-hadoop1-scala2.11.tgz | tar -xz -C /tmp
RUN mv /tmp/spark-1.6.1-bin-hadoop1-scala2.11 /usr/lib/spark
ENV SPARK_HOME="/usr/lib/spark"

# Spark initialization script
COPY start-master-slave.sh $SPARK_HOME/sbin
RUN chmod +x $SPARK_HOME/sbin/start-master-slave.sh

# Variable PATH
ENV PATH="$SPARK_HOME/sbin:$SPARK_HOME/bin:${PATH}"

ENV SPARK_MASTER_IP=0.0.0.0