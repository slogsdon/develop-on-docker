FROM debian:jessie

# USER
ENV SHELL /bin/zsh
ENV USER user
ENV HOME /home/$USER

RUN \
    apt-get update &&\
    apt-get install -y \
      autoconf \
      automake \
      build-essential \
      cmake \
      curl \
      g++ \
      git \
      libssl-dev \
      libtool \
      libtool-bin \
      pkg-config \
      python-dev python-pip python3-dev python3-pip \
      stow \
      sudo \
      tmux \
      unzip \
      zsh \
      &&\
    git clone https://github.com/neovim/neovim &&\
    cd neovim &&\
    make CMAKE_BUILD_TYPE=Release &&\
    make install &&\
    cd .. &&\
    rm -rf ./neovim &&\
    chsh -s /bin/zsh &&\
    pip3 install neovim &&\
    pip2 install neovim &&\
    apt-get autoremove -y && apt-get clean -y &&\
    rm -rf /var/lib/apit/lists &&\
    adduser --disabled-password -m $USER &&\
    adduser $USER sudo &&\
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

WORKDIR $HOME
USER $USER

ENTRYPOINT ["$SHELL", "-c", "STOW_INSTALL=\"$HOME/.dotfiles/scripts/install.sh\"; [[ -f $STOW_INSTALL ]] && bash $STOW_INSTALL &>/dev/null; zsh -i"]
