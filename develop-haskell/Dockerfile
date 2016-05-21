FROM slogsdon/develop-base

RUN \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 575159689BEFB442 &&\
    echo 'deb http://download.fpcomplete.com/debian jessie main' | tee /etc/apt/sources.list.d/fpco.list &&\
    apt-get update &&\
    apt-get install -y \
      stack \
      libgmp-dev \
      xz-utils \
      zlib1g-dev \
      &&\
    stack setup
