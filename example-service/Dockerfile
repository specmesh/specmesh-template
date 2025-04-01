FROM amazoncorretto:24@sha256:d59b1a52cb7e6e97bb888d4152ddc88563106262bc5d1324f6884bd07a1ebf71
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