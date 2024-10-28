FROM ubuntu:24.04
LABEL maintainer="ffalanges"
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get dist-upgrade -y && apt-get install -y software-properties-common systemd && rm -fr /var/lib/apt/lists/*
RUN apt-get update && apt install -y \
  git \
  apt-transport-https \
  curl \
  init \
  openssh-server openssh-client wget \
  vim \
  net-tools \
  && rm -fr /var/lib/apt/lists/*
EXPOSE 80

COPY ./scripts/install_nginx.sh /data/install_nginx.sh
RUN chmod +x /data/install_nginx.sh
RUN /data/install_nginx.sh
ENTRYPOINT [ "/lib/systemd/systemd" ]
CMD ["/usr/bin/bash"]

