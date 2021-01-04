FROM jrei/systemd-ubuntu

RUN sed -i 's/# deb/deb/g' /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y  apt-transport-https ca-certificates sudo curl gnupg-agent software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN curl -fsSL https://download.docker.com/linux/ubuntu/gpg |  apt-key add -

RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"


RUN apt-get update \
    && apt-get install -y  docker-ce docker-ce-cli containerd.io \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
