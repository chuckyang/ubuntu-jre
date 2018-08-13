FROM ubuntu:16.04

#### change timezone ####
RUN apt-get update && apt-get install -y tzdata \
    && echo "Asia/Shanghai" > /etc/timezone \
    && rm /etc/localtime \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata
### install tools ####
RUN apt-get update && \
    apt-get install -y iputils-ping && \
    apt-get install -y net-tools

###i nstall server jdk ####

ENV JAVA_VERSION "8u181"
ENV BUILD_VERSION "b13"
ENV JDK_VERSION "1.8.0_181"
ENV MD5=96a7b8442fe848ef90c96a2fad6ed6d1
RUN apt-get update && apt-get install -y \
    wget \
    curl \
    vim \
    && mkdir -p /usr/lib/jvm \
    && cd /usr/lib/jvm \
    && wget --no-cookies --no-check-certificate --header "Cookie:oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}-${BUILD_VERSION}/$MD5/server-jre-${JAVA_VERSION}-linux-x64.tar.gz" \
    && tar -zxvf server-jre-${JAVA_VERSION}-linux-x64.tar.gz \
    && rm /usr/lib/jvm/server-jre-${JAVA_VERSION}-linux-x64.tar.gz \
    && ln -s /usr/lib/jvm/jdk${JDK_VERSION}/bin/java /bin/ \
    && cd /usr/lib/jvm/jdk${JDK_VERSION} \
    && find . -type f -name '*.html' -delete \
    && find . -type f -name '*.bat' -delete \
    && find . -type f -name 'COPYRIGHT' -delete \
    && find . -type f -name 'LICENSE' -delete \
    && find . -type f -name 'NOTICE' -delete \
    && find . -type f -name '3RDPARTY' -delete \
    && find . -type f -name 'THIRDPARTYLICENSE.txt' -delete \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
