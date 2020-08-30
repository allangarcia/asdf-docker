FROM archlinux
RUN pacman -Syu --noconfirm && \
    pacman -S base-devel zsh git vim --noconfirm && \
    git clone https://github.com/asdf-vm/asdf.git ~/.asdf && \
    cd ~/.asdf && \
    git checkout -d "$(git describe --abbrev=0 --tags)" && \
    sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" && \
    sed -i 's/plugins=\(.*\)/plugins=\(git asdf archlinux\)/' ~/.zshrc
WORKDIR /root
SHELL [ "/bin/zsh", "-c" ]
ENTRYPOINT [ "/bin/zsh", "-l" ]