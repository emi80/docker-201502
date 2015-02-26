# Dockerfile
#

FROM       debian:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y --no-install-recommends \
      apt-utils \
      samtools \
    && rm -rf /var/lib/apt/lists/*
