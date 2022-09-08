## 使用replay-blockchain进行重播

```sh
docker run --name eosio-replay \
  --publish 7777:7777 \
  --publish 127.0.0.1:5555:5555 \
  --detach \
  --network t-net \
  --network-alias eos \
  -v /Users/apple/works/docker/contracts:/contracts \
  -v /Users/apple/works/docker/eos-db/configmap:/opt/eos/bin/config-dir/ \
  -v /Users/apple/works/docker/eos-db/data:/opt/eos/bin/data-dir/ \
  eosio/eos:release_2.1.x \
  /bin/bash -c \
    "keosd --http-server-address=0.0.0.0:5555 \
           --unlock-timeout=86400 & \
     exec nodeos --replay-blockchain \
       --config-dir /opt/eos/bin/config-dir \
       --data-dir /opt/eos/bin/data-dir
       >> nodeos.log 2>&1 &"
  
```

## 使用hard-replay-blockchain进行重播

```sh
docker run --name eosio-replay \
  --publish 7777:7777 \
  --publish 127.0.0.1:5555:5555 \
  --detach \
  --network t-net \
  --network-alias eos \
  -v /Users/apple/works/docker/contracts:/contracts \
  -v /Users/apple/works/docker/eos-db/configmap:/opt/eos/bin/config-dir/ \
  -v /Users/apple/works/docker/eos-db/data:/opt/eos/bin/data-dir/ \
  eosio/eos:release_2.1.x \
  /bin/bash -c \
    "keosd --http-server-address=0.0.0.0:5555 \
           --unlock-timeout=86400 & \
     exec nodeos --hard-replay-blockchain \
       --config-dir /opt/eos/bin/config-dir \
       --data-dir /opt/eos/bin/data-dir
       >> nodeos.log 2>&1 &"
  
```
## 使用快照进行重播

```sh
docker run --name eosio \
  --publish 7777:7777 \
  --publish 127.0.0.1:5555:5555 \
  --detach \
  --network t-net \
  --network-alias eos \
  -v /Users/apple/works/docker/contracts:/contracts \
  -v /Users/apple/works/docker/eos-db/configmap:/opt/eos/bin/config-dir/ \
  -v /Users/apple/works/docker/eos-db/data:/opt/eos/bin/data-dir/ \
  eosio/eos:release_2.1.x \
  /bin/bash -c \
    "keosd --http-server-address=0.0.0.0:5555 \
           --unlock-timeout=86400 & \
     exec nodeos \
       --config-dir /opt/eos/bin/config-dir \
       --data-dir /opt/eos/bin/data-dir \
       --delete-all-blocks \
       --snapshot /opt/eos/bin/data-dir/snapshots/snapshot-000014c94aceac08711156bf9c98b86fcb3fc10aa87bf11ce856beab91c3458b.bin
       >> nodeos.log 2>&1 &"
  
```
