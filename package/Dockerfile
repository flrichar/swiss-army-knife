FROM ubuntu:24.04
RUN sed -i 's:^path-exclude=/usr/share/man:#path-exclude=/usr/share/man:' /etc/dpkg/dpkg.cfg.d/excludes
RUN apt-get update && \
    export DEBIAN_FRONTEND=noninteractive && \
    apt-get install --no-install-recommends -y \
        arping \
        arptables \
        bridge-utils \
        ca-certificates \
        conntrack \
        curl \
        dnsutils \
        ethtool \
        iperf \
        iperf3 \
        iproute2 \
        ipset \
        iptables \
        iputils-ping \
        jq \
        kmod \
        ldap-utils \
        less \
        libpcap-dev \
        man \
        manpages-posix \
        mtr \
        net-tools \
        ncat \
        netcat-traditional \
        openssl \
        openssh-client \
        psmisc \
        socat \
        tcpdump \
        telnet \
        tmux \
        traceroute \
        tcptraceroute \
        tree \
        ngrep \
        vim \
        wireguard-tools \
        wget && \
    rm -rf /var/lib/apt/lists/* && \
    curl -sL https://github.com/containerd/nerdctl/releases/download/v1.7.6/nerdctl-1.7.6-linux-amd64.tar.gz | tar Czxv /usr/bin/ nerdctl && \
    chmod +x /usr/bin/nerdctl && \
    curl -sLf https://storage.googleapis.com/kubernetes-release/release/v1.28.13/bin/linux/amd64/kubectl > /usr/local/bin/kubectl-1.28 && \
    curl -sLf https://storage.googleapis.com/kubernetes-release/release/v1.29.8/bin/linux/amd64/kubectl > /usr/local/bin/kubectl-1.29 && \
    curl -sLf https://storage.googleapis.com/kubernetes-release/release/v1.30.4/bin/linux/amd64/kubectl > /usr/local/bin/kubectl-1.30 && \
    chmod +x /usr/local/bin/kubectl* && \
    ln -s /usr/local/bin/kubectl-1.29 /usr/local/bin/kubectl && \
    wget https://github.com/mikefarah/yq/releases/download/v4.44.3/yq_linux_amd64 -O /usr/bin/yq && \
    chmod +x /usr/bin/yq && \
    mkdir -p /root/.kube

ENV LOGLEVEL_TAG v0.1.6
RUN curl -sfSL https://github.com/rancher/loglevel/releases/download/${LOGLEVEL_TAG}/loglevel-amd64-${LOGLEVEL_TAG}.tar.gz | tar xvzf - -C /usr/bin
COPY swiss-army-knife /usr/bin/
WORKDIR /root
CMD ["swiss-army-knife"]
