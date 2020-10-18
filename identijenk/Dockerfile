FROM jenkins/jenkins
USER root

RUN apt-get update \
      && apt-get install -y apt-utils apt-transport-https ca-certificates curl gnupg-agent software-properties-common \
      && curl -fsSL "https://download.docker.com/linux/debian/gpg" | apt-key add - \
      && add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/debian \
       $(lsb_release -cs) \
       stable" \
      && apt-get update \
      && apt-get install -y sudo \
      && apt-get install -y --allow-downgrades docker-ce docker-ce-cli containerd.io \
      && apt-get install -y --allow-downgrades docker-ce=5:18.09.1~3-0~debian-stretch docker-ce-cli=5:18.09.1~3-0~debian-stretch containerd.io \
      && rm -rf /var/lib/apt/lists/*
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose; \
      chmod +x /usr/local/bin/docker-compose

USER jenkins
COPY plugins.txt /usr/share/jenkins/plugins.txt

