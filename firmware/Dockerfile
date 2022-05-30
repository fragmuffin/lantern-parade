FROM ubuntu:18.04

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -qq \
 && apt-get install -y software-properties-common apt-utils \
 && add-apt-repository -y ppa:team-gcc-arm-embedded/ppa \
 && apt-get update -qq \
 && apt-get install -y build-essential gcc-arm-embedded cmake git

# Build requires python >= 3.8
RUN apt-get install -y python3.8 \
 && ln -fs python3.8 /usr/bin/python3

# This always returns errorcode 100, so check it's installed
RUN apt-get install -y libnewlib-arm-none-eabi || true \
 && arm-none-eabi-gcc --version

WORKDIR /code/firmware/micropython-microbit-v2
