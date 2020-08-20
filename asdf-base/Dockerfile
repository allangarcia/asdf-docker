FROM archlinux
RUN pacman -Syu --noconfirm
RUN pacman -S git vim --noconfirm
RUN git clone https://github.com/asdf-vm/asdf.git ~/.asdf && \
    cd ~/.asdf && \
    git checkout -d "$(git describe --abbrev=0 --tags)" && \
    echo '. $HOME/.asdf/asdf.sh' > ~/.bashrc && \
    echo '. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc
WORKDIR /root
SHELL ["/bin/bash", "-c"]