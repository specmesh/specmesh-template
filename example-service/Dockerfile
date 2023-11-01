FROM amazoncorretto:21@sha256:753ab43b764c70d53d44785b8720d43333ab45ccc422825ac30147c28ea97e88
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