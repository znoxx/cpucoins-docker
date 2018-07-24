FROM debian:sid
LABEL description="Verium cpu miner by rollmeister with nice value setting built with gcc8."

RUN set -x \
    && BUILD_DEPS="automake autoconf ca-certificates pkg-config libssl-dev libgmp-dev zlib1g-dev gcc-8 g++-8 git make" \
    && apt-get update \
    && apt-get upgrade -y \
    && apt-get --no-install-recommends install -y libcurl4-openssl-dev libjansson-dev $BUILD_DEPS \
    && git clone https://github.com/rollmeister/veriumMiner \
    && cd veriumMiner \
    && ./autogen.sh \
    && ./configure CC="gcc-8" CXX="g++-8" CFLAGS="-O3 -mcpu=cortex-a53 -flto -fuse-linker-plugin -funroll-loops" CXXFLAGS="-O3 -mcpu=cortex-a53 -flto -fuse-linker-plugin -funroll-loops" RANLIB="aarch64-linux-gnu-gcc-ranlib-8 --plugin=$(gcc-8 --print-file-name=liblto_plugin.so)" ARFLAGS="cr --plugin=$(gcc-8 --print-file-name=liblto_plugin.so)" --with-curl --with-crypto \
    && make RANLIB="aarch64-linux-gnu-gcc-ranlib-8 --plugin=$(gcc-8 --print-file-name=liblto_plugin.so)" ARFLAGS=" cr --plugin=$(gcc-8 --print-file-name=liblto_plugin.so)" LDFLAGS="-O3 -mcpu=cortex-a53 -flto -fuse-linker-plugin -funroll-loops" AR="aarch64-linux-gnu-gcc-ar-8" \
    && apt-get -y --auto-remove purge $BUILD_DEPS \
    && rm -fr /var/lib/apt-/lists/*
ENV NICEVALUE 10
COPY ./runminer /
ENTRYPOINT ["./runminer"]




