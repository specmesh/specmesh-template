FROM amazoncorretto:21@sha256:582fbf5a116eca7e2f9d1bc0e1888e121eebb980e929270c28f8e6a33fea2d6f
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