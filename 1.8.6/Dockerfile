FROM ubuntu
####change timezone####
RUN apt-get update && apt-get install -y tzdata \
    && echo "Asia/Shanghai" > /etc/timezone \
    && rm /etc/localtime \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata
###install tools####
RUN apt-get update && \
    apt-get install -y iputils-ping && \
    apt-get install -y net-tools

###install jre####

ENV JAVA_VERSION "8u162"
ENV BUILD_VERSION "b12"
ENV JDK_VERSION "1.8.0_162"

RUN apt-get update && apt-get install -y \
    wget \
    curl \
    && mkdir -p /usr/lib/jvm \
    && cd /usr/lib/jvm \
    && wget --no-cookies --no-check-certificate --header "Cookie:oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/${JAVA_VERSION}-${BUILD_VERSION}/0da788060d494f5095bf8624735fa2f1/server-jre-${JAVA_VERSION}-linux-x64.tar.gz" \
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
