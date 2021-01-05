FROM ubuntu-systemd-docker

RUN sed -i 's/# deb/deb/g' /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y apt-transport-https curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -

RUN echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" >>  /etc/apt/sources.list.d/kubernetes.list

RUN apt-get update \
    && apt-get install -y kubelet kubeadm kubectl inetutils-ping haproxy  \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN apt-mark hold kubelet kubeadm kubectl

RUN echo 'Environment="KUBELET_EXTRA_ARGS=--fail-swap-on=false"' >> /etc/systemd/system/kubelet.service.d/10-kubeadm.conf
#RUN kubeadm config images pull

#RUN systemctl daemon-reload
#RUN systemctl restart kubelet
