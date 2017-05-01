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

RUN pacman -S --needed --noconfirm arpack blas fftw hwloc intel-tbb lapack libgit2 metis numactl openmpi \
     patchelf pcre2 suitesparse \
  && cd /home/docker/sandground \
  && wget https://archive.archlinux.org/packages/j/julia/julia-2:0.4.6-1-x86_64.pkg.tar.xz \
  && pacman --needed --noconfirm -U julia-2:0.4.6-1-x86_64.pkg.tar.xz 

RUN cd /home/docker/sandground \
  && pacman -S --needed --noconfirm cargo \
  && git clone https://github.com/ararslan/julia-pkg \
  && cd julia-pkg \
  && make install
  
RUN julia-pkg install --git https://github.com/imriss/ManifoldLearning.jl 

RUN echo `julia /root/.julia/v0.4/ManifoldLearning/test/lle.jl`

RUN echo "`ls /root/ -la`" \
  && echo "`ls /home/docker/ -la`"
  
RUN echo `(pacman -Qetq) <(pacman -Qgq base julia | sort)`

RUN rm -rd /home/docker/sandground
  
