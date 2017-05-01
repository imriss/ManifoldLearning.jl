FROM imriss/archlinux

RUN echo 'ManifoldLearning Julia on Arch Linux'

MAINTAINER Reza Farrahi <imriss@ieee.org>
LABEL description="ManifoldLearning Julia / Arch Linux"

RUN  pacman -Syyu --noconfirm \
  && pacman -S findutils nano vi --needed --noconfirm \
  && pacman-db-upgrade \
  && export editor=nano \
  && pacman -S --needed --noconfirm wget gnuplot llvm39 
  
RUN cd /home/docker \
  && mkdir sandground \
  && cd sandground \
  && wget https://archive.archlinux.org/packages/j/julia/julia-2%3A0.4.6-1-x86_64.pkg.tar.xz \
  && pacman -U julia-2%3A0.4.6-1-x86_64.pkg.tar.xz 

RUN echo `ls /root/ -la` \
  && echo `ls /home/docker/ -la`
  
  
