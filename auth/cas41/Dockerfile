FROM java:8-jdk

RUN apt-get update \
    && apt-get install -y \
      git \
      maven \
    && apt-get clean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /cas

ADD ./cas /cas
ADD ./cas/etc /etc/cas
RUN mvn clean install -DskipTests=true

EXPOSE 8080
EXPOSE 8443

CMD ["/usr/bin/mvn", "jetty:run"]
