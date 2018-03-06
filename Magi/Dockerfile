FROM ubuntu:16.04
LABEL description="Magi cpu miner with nice value setting."
RUN set -x \
    && BUILD_DEPS="automake autoconf ca-certificates pkg-config libssl-dev libgmp-dev zlib1g-dev g++ git" \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get --no-install-recommends install -y libcurl4-openssl-dev libjansson-dev $BUILD_DEPS \
    && git clone https://github.com/magi-project/wolf-m7m-cpuminer-V2 \
    && cd wolf-m7m-cpuminer-V2 \
    && sed -i -e 's/-flto -fuse-linker-plugin//g' Makefile.am \
    && sed -i -e 's/-flto//g' m7/Makefile.am \
    && ./autogen.sh && ./configure CFLAGS="-O3" CXXFLAGS="-O3" && make \
    && apt-get -y --auto-remove purge $BUILD_DEPS \
    && rm -fr /var/lib/apt-/lists/*
ENV NICEVALUE 10
COPY ./runminer /
ENTRYPOINT ["./runminer"]
