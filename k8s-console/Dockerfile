FROM debian:unstable
WORKDIR /root
# default shell env
SHELL [ "/bin/bash", "-c" ]
# Update the system and install basic packages
RUN apt update -y && \
    apt upgrade -y && \
    apt install bash-completion -y && \
    apt install git -y && \
    apt install vim -y && \
    apt install curl -y
# Enable colors on ls and some default aliases
RUN sed -i '9,13s/^# //' /root/.bashrc && \
    sed -i '16,18s/^# //' /root/.bashrc && \
    sed -i 's/dircolors/dircolors -b/' /root/.bashrc
# Install asdf
RUN git clone https://github.com/asdf-vm/asdf.git ~/.asdf && \
    cd ~/.asdf && \
    git checkout -d "$(git describe --abbrev=0 --tags)" && \
    cd && \
    sed -i '$ a # Add support to asdf\n. $HOME/.asdf/asdf.sh\n. $HOME/.asdf/completions/asdf.bash' .bashrc && \
    source .bashrc
# Install build dependencies
RUN apt install build-essential -y && \
    apt install zlib1g-dev -y && \
    apt install libssl-dev -y && \
    apt install libreadline-dev && \
    apt install libbz2-dev && \
    apt install libncursesw5-dev && \
    apt install libgdbm-dev && \
    apt install liblzma-dev && \
    apt install libsqlite3-dev && \
    apt install uuid-dev
# Install python
RUN asdf install python 3.9.1 && \
    asdf global python 3.9.1 && \
    asdf reshim python 3.9.1
# kubectl download, install, and clean
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && \
    curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256" && \
    echo "`cat kubectl.sha256` kubectl" | sha256sum --check && \
    install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && \
    rm -rf kubectl*
# kubectl command completion
RUN mkdir -p /etc/bash_completion.d && \
    kubectl completion bash >/etc/bash_completion.d/kubectl
# set entrypoint for docker run -i
ENTRYPOINT [ "/bin/bash", "-l" ]