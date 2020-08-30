FROM allangarcia/asdf-nodejs
RUN source ~/.zshrc && \
    asdf plugin-add ruby https://github.com/asdf-vm/asdf-ruby.git && \
    asdf install ruby 2.7.1 && \
    asdf global ruby 2.7.1 && \
    gem install rails
WORKDIR /Developer
