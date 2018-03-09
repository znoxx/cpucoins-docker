FROM ubuntu:17.10
LABEL description="Electroneum cpu miner with nice value setting built with GCC7."

RUN set -x \
    && BUILD_DEPS="git build-essential cmake" \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get --no-install-recommends install -y ca-certificates libuv1-dev libmicrohttpd-dev $BUILD_DEPS \
    && git clone https://github.com/xmrig/xmrig.git \
    && cd xmrig \
    && mkdir build \
    && cd build \
    && cmake .. \
    && make \
    && apt-get -y --auto-remove purge $BUILD_DEPS \
    && rm -fr /var/lib/apt-/lists/*
ENV NICEVALUE 10
COPY ./runminer /
ENTRYPOINT ["./runminer"]




