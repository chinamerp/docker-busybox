FROM ubuntu:12.04

ADD ./config /tmp/config
RUN locale-gen en_US.UTF-8

RUN apt-get update -q
RUN apt-get install -qy wget build-essential libncurses-dev rsync unzip bc git
RUN wget http://buildroot.uclibc.org/downloads/buildroot-2014.08.tar.gz
RUN echo 'fe98057ce78ef39092e38652b055604a  buildroot-2014.08.tar.gz' > buildroot.md5
RUN md5sum --check buildroot.md5
RUN tar -zxf buildroot-2014.08.tar.gz
WORKDIR /buildroot-2014.08
RUN mv /tmp/config ./.config
RUN make oldconfig
RUN make
RUN ln -s /buildroot-2014.08/output/images/rootfs.tar /rootfs.tar
