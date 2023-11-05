FROM ubuntu:jammy

#base
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update
RUN apt-get install -y apt-utils sudo locales tzdata \
    iputils-ping net-tools jq tzdata curl python3 gcc make sqlite3 \
    g++ git\
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG ja_JP.UTF-8
ENV LC_ALL ja_JP.UTF-8
ENV LANGUAGE ja_JP:ja
ENV TZ Asia/Tokyo

RUN groupadd -g 1000 scala-user \
    && useradd -u 1000 -g 1000 -m scala-user \
    && gpasswd -a scala-user sudo \
    && echo "scala-user:passwd" | chpasswd \
    && echo "root:passwd" | chpasswd

RUN apt-get update
RUN apt-get install -y openjdk-17-jre-headless

RUN curl -fL https://github.com/Virtuslab/scala-cli/releases/latest/download/scala-cli-x86_64-pc-linux.gz | gzip -d > scala-cli \
    && chmod +x scala-cli \
    && mv scala-cli /usr/local/bin/scala-cli \
    && scala-cli --version

RUN curl -fL "https://github.com/coursier/launchers/raw/master/cs-x86_64-pc-linux.gz" | gzip -d > cs \
    && chmod +x cs \
    && mv cs /usr/local/bin/cs 

RUN cs install ammonite

USER scala-user

CMD ["bash"]