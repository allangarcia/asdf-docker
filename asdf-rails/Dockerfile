FROM allangarcia/asdf-base
RUN source ~/.zshrc && \
    asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git && \
    bash -c '${ASDF_DATA_DIR:=$HOME/.asdf}/plugins/nodejs/bin/import-release-team-keyring' && \
    asdf install nodejs 14.8.0 && \
    asdf global nodejs 14.8.0 && \
    asdf plugin-add ruby https://github.com/asdf-vm/asdf-ruby.git && \
    asdf install ruby 2.7.1 && \
    asdf global ruby 2.7.1 && \
    gem install rails
WORKDIR /Developer