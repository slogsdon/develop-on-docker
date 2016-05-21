FROM debian:jessie

# USER
ENV SHELL /bin/zsh
ENV USER user
ENV HOME /home/$USER

RUN \
    apt-get update &&\
    apt-get install -y \
      tmux \
      zsh \
      curl \
      stow \
      python-dev python-pip python3-dev python3-pip \
      libssl-dev \
      libtool \
      libtool-bin \
      autoconf \
      automake \
      cmake \
      g++ \
      pkg-config \
      build-essential \
      unzip \
      git \
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
    useradd -m $USER

WORKDIR $HOME
USER $USER

ENTRYPOINT ["$SHELL", "-c", "STOW_INSTALL=\"$HOME/.dotfiles/scripts/install.sh\"; [[ -f $STOW_INSTALL ]] && bash $STOW_INSTALL &>/dev/null; zsh -i"]
