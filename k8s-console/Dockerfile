FROM debian:unstable
WORKDIR /root
# Update the system and install basic packages
RUN apt update -y && \
    apt upgrade -y && \
    apt install vim -y && \
    apt install bash-completion -y && \
    apt install curl -y
# Enable colors on ls and some default aliases
RUN sed -i '9,13s/^# //' /root/.bashrc && \
    sed -i '16,18s/^# //' /root/.bashrc && \
    sed -i 's/dircolors/dircolors -b/' /root/.bashrc
# kubectl download, install, and clean
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" && \
    curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256" && \
    echo "`cat kubectl.sha256` kubectl" | sha256sum --check && \
    install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl && \
    rm -rf kubectl*
# kubectl command completion
RUN mkdir -p /etc/bash_completion.d && \
    kubectl completion bash >/etc/bash_completion.d/kubectl
# default shell env
SHELL [ "/bin/bash", "-c" ]
ENTRYPOINT [ "/bin/bash", "-l" ]