# Dockerfile
#

FROM       debian:latest

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    samtools \
    && rm -rf /var/lib/apt/lists/*
