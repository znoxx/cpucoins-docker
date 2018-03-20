# Some Dockerfiles for various cpu-mineable coins #

Start mining of cpu-mineable coins on almost any docker-enabled linux.

### Coins ###

* Zoin -- https://github.com/zoinofficial/cpuminer-zoin
* Verium -- https://github.com/fireworm71/veriumMiner
* Magi -- https://github.com/magi-project/wolf-m7m-cpuminer-V2
* Electroneum -- https://github.com/xmrig/xmrig

### Quick start ###

Clone repo. Change to desired folder. Run:
```
docker build .
```
Then, start your miner with:

```
docker run -e NICEVALUE=desired_nice_value image_id miner_options
```
For example:

```
cd Zoin
docker build .
docker run -e NICEVALUE=13 2377ba0f1c00 -a lyra2zoin -o  stratum+tcp://zoin.netabuse.net:3000 -u your_pool_id.worker -p worker_password
```

Exact miner options depend on particular miner. Please check official doc/pool start guide

### Pre-built images

|arch/coin|armhf|gcc7_armhf|arm64|gcc7_arm64|x86_64|gcc7_x86_64|gcc7_neon_armhf|
|---------|-----|----------|-----|----------|------|-----------|---------------|
|zoin|[OK](https://hub.docker.com/r/znoxx/zoinminer_armhf/)|[OK](https://hub.docker.com/r/znoxx/zoinminer_gcc7_armhf/)|N/A|N/A|[OK](https://hub.docker.com/r/znoxx/zoinminer_x86_64/)|[OK](https://hub.docker.com/r/znoxx/zoinminer_gcc7_x86_64/)|[OK](https://hub.docker.com/r/znoxx/zoinminer_gcc7_neon_armhf/)|
|verium|[OK](https://hub.docker.com/r/znoxx/veriumminer_armhf/)|[OK](https://hub.docker.com/r/znoxx/veriumminer_gcc7_armhf/)|[OK](https://hub.docker.com/r/znoxx/veriumminer_arm64/)|[OK](https://hub.docker.com/r/znoxx/veriumminer_gcc7_arm64/)|TBD|[OK](https://hub.docker.com/r/znoxx/veriumminer_gcc7_x86_64/)|[OK](https://hub.docker.com/r/znoxx/veriumminer_gcc7_neon_armhf/)|
|electroneum|[OK](https://hub.docker.com/r/znoxx/electroneumminer_armhf/)|[OK](https://hub.docker.com/r/znoxx/electroneumminer_gcc7_armhf/)|[OK](https://hub.docker.com/r/znoxx/electroneumminer_arm64/)|N/A|TBD|TBD|TBD|
|magi|[OK](https://hub.docker.com/r/znoxx/magiminer_armhf/)|[OK](https://hub.docker.com/r/znoxx/magiminer_gcc7_armhf/)|[OK](https://hub.docker.com/r/znoxx/magiminer_arm64/)|[OK](https://hub.docker.com/r/znoxx/magiminer_gcc7_arm64/)|TBD|TBD|TBD|
|cpuminer-opt|N/A|N/A|N/A|N/A|N/A|[OK](https://hub.docker.com/r/znoxx/cpuminer-opt_gcc7_x86_64/)|N/A|

#### Happy mining!