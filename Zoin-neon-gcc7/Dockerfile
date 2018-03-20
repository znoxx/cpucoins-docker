FROM ubuntu:17.10
LABEL description="Zoin cpu-miner with nice value setting built with neon extensions and GCC7."

RUN set -x \
    && BUILD_DEPS="automake autoconf ca-certificates pkg-config libssl-dev libgmp-dev zlib1g-dev build-essential git" \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get --no-install-recommends install -y libcurl4-openssl-dev libjansson-dev $BUILD_DEPS \
    && git clone https://github.com/zoinofficial/cpuminer-zoin \
    && cd cpuminer-zoin \
    && sed -i -e 's/-DUSE_ASM -pg/-DUSE_ASM -mfpu=neon-vfpv4 -pg/g' build.sh \
    && ./build.sh \
    && apt-get -y --auto-remove purge $BUILD_DEPS \
    && rm -fr /var/lib/apt-/lists/*
ENV NICEVALUE 10
COPY ./runminer /
ENTRYPOINT ["./runminer"]




