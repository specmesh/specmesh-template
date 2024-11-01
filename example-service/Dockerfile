FROM amazoncorretto:23@sha256:915d033a225e05edde9b1f184b0ff1f8f231d8580cceb22dfb90d48a496270c2
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