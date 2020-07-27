FROM ubuntu:18.04

MAINTAINER Jim-tech <xx@xx>

#COPY .vim /root/
#COPY .vimrc /root/
COPY sources.list /etc/apt/sources.list

RUN apt-get clean
RUN dpkg --add-architecture i386
RUN apt-get update

RUN apt-get install -y udev vim wget axel openssh-server net-tools wine-stable wine32 build-essential make default-jre git ctags cscope

RUN echo 'export DISPLAY=host.docker.internal:0.0' >> /etc/bash.bashrc
RUN echo 'PermitRootLogin yes' >>/etc/ssh/sshd_config
RUN echo root:123 | chpasswd
RUN echo 'if [ ! -e /tmp/.ssh_service ]; then' >> /etc/bash.bashrc
RUN echo '    echo 1 > /tmp/.ssh_service' >> /etc/bash.bashrc
RUN echo '    /etc/init.d/ssh start' >> /etc/bash.bashrc
RUN echo 'fi' >> /etc/bash.bashrc
# RUN git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim


RUN axel -a -n 8 -o /opt/ https://www.silabs.com/documents/login/software/SimplicityStudio-v4.tgz
RUN cd /opt && tar zxvf SimplicityStudio-v4.tgz && rm -rf SimplicityStudio-v4.tgz
RUN sed -i s/sudo//g /opt/SimplicityStudio_v4/setup.sh
RUN cd /opt/SimplicityStudio_v4/ && yes | ./setup.sh
