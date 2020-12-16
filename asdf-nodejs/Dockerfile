FROM allangarcia/asdf-base
RUN source ~/.zshrc && \
    asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git && \
    zsh -c '${ASDF_DATA_DIR:=$HOME/.asdf}/plugins/nodejs/bin/import-release-team-keyring' && \
    asdf install nodejs 15.4.0 && asdf global nodejs 15.4.0
WORKDIR /Developer
