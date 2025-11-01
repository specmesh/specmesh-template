FROM amazoncorretto:25@sha256:2dc9c6aabe47fa1017b854b1d7cf9373e5469d8af56a89f7e7498e8205415656
ARG APP_NAME
ARG APP_VERSION
ENV VERSION=$APP_VERSION

LABEL org.opencontainers.image.source=https://github.com/specmesh/specmesh-template

RUN yum update -y
RUN yum install -y tar lsof

RUN mkdir -p /opt/specmesh

COPY bin /bin
COPY log4j /log

COPY ${APP_NAME}-${APP_VERSION}.tar /opt/specmesh
WORKDIR /opt/specmesh
RUN tar xf ${APP_NAME}-${APP_VERSION}.tar
RUN ln -s ${APP_NAME}-${APP_VERSION} service

ENTRYPOINT ["/bin/run.sh"]