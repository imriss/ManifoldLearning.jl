FROM imriss/archlinux

RUN echo 'ManifoldLearning Julia on Arch Linux'

MAINTAINER Reza Farrahi <imriss@ieee.org>
LABEL description="ManifoldLearning Julia / Arch Linux"

RUN  pacman -Syyu --noconfirm \
  && pacman -S findutils nano vi --needed --noconfirm \
  && pacman-db-upgrade \
  && export editor=nano \
  && pacman -S --needed --noconfirm git wget gnuplot \
  && git config --global url."https://".insteadOf git:// 

# DDADD https://raw.githubusercontent.com/imriss/scylla/master/aur.sh /usr/sbin/aur.sh
# DDADD https://raw.githubusercontent.com/imriss/scylla/master/add-aur.sh /usr/sbin/add-aur
ADD ./aur.sh /usr/sbin/aur.sh
ADD ./add-aur.sh /usr/sbin/add-aur
RUN chmod u+x /usr/sbin/aur.sh
RUN chmod u+x /usr/sbin/add-aur
RUN add-aur docker

# RUN su docker -c 'pacaur -S --needed --noprogressbar --noedit --noconfirm julia'

RUN cd /home/docker \
  && mkdir sandground \
  && cd sandground \
  && wget https://archive.archlinux.org/packages/j/julia/julia-2%3A0.4.6-1-x86_64.pkg.tar.xz \
  && pacman -U julia-2%3A0.4.6-1-x86_64.pkg.tar.xz 

RUN echo `ls /root/ -la` \
  && echo `ls /home/docker/ -la`
  
  
