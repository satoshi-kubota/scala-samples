FROM sbtscala/scala-sbt:eclipse-temurin-jammy-20.0.2_9_1.9.6_3.3.1
RUN curl -fL https://github.com/Virtuslab/scala-cli/releases/latest/download/scala-cli-x86_64-pc-linux.gz | gzip -d > scala-cli
RUN chmod +x scala-cli
RUN sudo mv scala-cli /usr/local/bin/scala-cli