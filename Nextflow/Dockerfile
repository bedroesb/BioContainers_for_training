FROM openjdk:8-jre-alpine
MAINTAINER Paolo Di Tommaso <paolo.ditommaso@gmail.com>
ENV PATH=$PATH:/opt/bowtie:/opt/tophat:/opt/cufflinks

# Add required dependencies
# - bash 
# - gnu coreutils 
# - curl 
RUN apk update && apk add bash && apk add coreutils && apk add curl
RUN apt-get update --fix-missing && \
  apt-get install -q -y samtools python 

# see https://blogs.oracle.com/java-platform-group/java-se-support-for-docker-cpu-and-memory-limits
ENV NXF_OPTS='-XX:+UnlockExperimentalVMOptions -XX:+UseCGroupMemoryLimitForHeap' NXF_HOME=/.nextflow

# copy docker client
COPY dist/docker /usr/local/bin/docker
COPY entry.sh /usr/local/bin/entry.sh
COPY nextflow /usr/local/bin/nextflow
COPY data /data

# download runtime
RUN mkdir /.nextflow \
 && touch /.nextflow/dockerized \
 && chmod 755 /usr/local/bin/nextflow \
 && chmod 755 /usr/local/bin/entry.sh \
 && nextflow info


# define the entry point
ENTRYPOINT ["/usr/local/bin/entry.sh"]