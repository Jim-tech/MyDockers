FROM ubuntu:18.04

MAINTAINER Jim-tech <xx@xx>

RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN apt-get clean
RUN dpkg --add-architecture i386
RUN apt-get update
RUN apt-get install -y udev vim wget axel openssh-server net-tools wine-stable build-essential gcc g++ make default-jre gawk curl unzip tar

# ADD https://www.silabs.com/documents/login/software/SimplicityStudio-v4.tgz
RUN axel -a -n 8 -o /opt/ https://www.silabs.com/documents/login/software/SimplicityStudio-v4.tgz
