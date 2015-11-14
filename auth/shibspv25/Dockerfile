FROM java:8-jdk

RUN apt-get update \
    && apt-get install -y \
      vim \
      curl \
      supervisor \
      # compile shibboleth sp
      # gcc \
      # libssl-dev \
      # build-essential \
      # libboost-dev \
      # libfcgi-dev \
      # liblog4shib-dev \
      # libmemcached-dev \
      # libsaml2-dev \
      # libssl-dev \
      # libxerces-c-dev \
      # libxml-security-c-dev \
      # libxmltooling-dev \
      # opensaml2-schemas \
      # xmltooling-schemas \

      libxerces-c3.1 \
      libxml-security-c17 \
      libxmltooling6 \
      opensaml2-schemas \
      xmltooling-schemas \
      libshibsp6 \
      libshibsp-plugins \
      shibboleth-sp2-common \
      shibboleth-sp2-utils \

      # hmmmmmmmm
      # build-essential \
      # libpcre3 \
      # libpcre3-dev \
      # libpcrecpp0 \
      # libssl-dev \
      # zlib1g-dev \

      # supervisor \
      # procps \
    && echo "done"
    # && apt-get clean \
    # && apt-get autoremove -y \
    # && rm -rf /var/lib/apt/lists/*

#RUN apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62
#RUN echo "deb http://nginx.org/packages/mainline/debian/ jessie nginx" >> /etc/apt/sources.list
#RUN echo "deb-src http://nginx.org/packages/mainline/debian/ jessie nginx" >> /etc/apt/sources.list

# WORKDIR /nginx
#
# RUN apt-get update
# RUN apt-get install -y dpkg-dev
# RUN apt-get source nginx
# RUN apt-get build-dep -y nginx
# RUN mkdir ./nginx
# RUN tar -xvf nginx_1.9.6-1~jessie.debian.tar.xz -C ./nginx

# RUN mkdir /opt/rebuildnginx && mkdir /opt/rebuildnginx/debs && \
#     cd /opt/rebuildnginx && \
#     apt-get source nginx && apt-get build-dep -y nginx && \
#     git clone https://github.com/nginx-shib/nginx-http-shibboleth.git && \
#     git clone https://github.com/openresty/headers-more-nginx-module.git

# Download Shibboleth IdP, verify the hash, and install
# grab gosu for easy step-down from root
# ENV SHIBBOLETH_SP_VERSION 2.5.5
# RUN apt-get update \
#     && apt-get install -y \
#         curl \
#     && gpg --keyserver pool.sks-keyservers.net --recv-keys 02277962 \
#     && curl -SLO "https://shibboleth.net/downloads/service-provider/$SHIBBOLETH_SP_VERSION/shibboleth-sp-$SHIBBOLETH_SP_VERSION.tar.gz" \
#     && curl -SLO "https://shibboleth.net/downloads/service-provider/$SHIBBOLETH_SP_VERSION/shibboleth-sp-$SHIBBOLETH_SP_VERSION.tar.gz.asc" \
#   	&& gpg --verify "shibboleth-sp-$SHIBBOLETH_SP_VERSION.tar.gz.asc" \
#     && mkdir /sp \
#     && tar -xzf "shibboleth-sp-$SHIBBOLETH_SP_VERSION.tar.gz" -C /sp --strip-components=1 \
#     && rm "shibboleth-sp-$SHIBBOLETH_SP_VERSION.tar.gz" \
#     && rm "shibboleth-sp-$SHIBBOLETH_SP_VERSION.tar.gz.asc" \
#     && echo "done"
#   	# && chmod +x "/usr/local/bin/gosu" \
#     # && apt-get clean \
#     # && apt-get autoremove -y \
#     #     curl \
#     # && rm -rf /var/lib/apt/lists/*

WORKDIR /sp

# JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::")
ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64/jre/

#RUN bin/install.sh -Didp.src.dir=/idp -Didp.target.dir=/opt/shibboleth-idp  -Didp.keystore.password=CHANGEME -Didp.sealer.password=CHANGEME -Didp.host.name=localhost.localdomain \
#     && chmod -R +r /opt/shibboleth-idp/ \
#     && sed -i 's/ password/CHANGEME/g' /opt/shibboleth-idp/conf/idp.properties \
#
# RUN set -x; \
#     shibidp_version=3.1.2; \
#     wget https://shibboleth.net/downloads/service-provider/$shibidp_version/shibboleth-service-provider-$shibidp_version.zip \
#     && echo "0c6747b28b1f76eb6fd1a1f2b9fce99c70e70be2e9ef0099f84a006673123027  shibboleth-service-provider-$shibidp_version.zip" | sha256sum -c - \
#     && unzip shibboleth-service-provider-$shibidp_version.zip -d /opt \
#     && cd /opt/shibboleth-service-provider-$shibidp_version/ \
#     && bin/install.sh -Didp.keystore.password=CHANGEME -Didp.sealer.password=CHANGEME -Didp.host.name=localhost.localdomain \
#     && cd / \
#     && chmod -R +r /opt/shibboleth-idp/ \
#     && sed -i 's/ password/CHANGEME/g' /opt/shibboleth-idp/conf/idp.properties \
#     && rm -r /shibboleth-service-provider-$shibidp_version.zip /opt/shibboleth-service-provider-$shibidp_version/
#
# ADD ./cas /cas
# ADD ./cas/etc /etc/cas
# RUN mvn clean install -DskipTests=true
#
# EXPOSE 8080
# EXPOSE 8443
#
# CMD ["/usr/bin/mvn", "jetty:run"]

VOLUME /opt/shibboleth-idp

CMD ["/bin/bash"]
