# eos-deploy-guide


 ## 下载docker镜像 
```sh
docker pull eosio/dev
```
如果下载不动或者报错,需要设置国内源

## 运行镜像
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
  eosio/dev \
  /bin/bash -c \
    "keosd --http-server-address=0.0.0.0:5555 \
           --unlock-timeout=86400 & \
     exec nodeos -e -p eosio \
       --config-dir /opt/eos/bin/config-dir \
       --data-dir /opt/eos/bin/data-dir"
 ```
 
 ## 配置钱包

### 1. 创建默认钱包
```sh
cleos wallet create --to-console
```
保存好控制台密码`PW5KDxNj1zVjMsQSBL1fdSFkfK9zyxDVmKAr7XWSStzgtYJaYfEqR`

### 2. 导入测试区块链key
```sh
cleos wallet import --private-key 5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3
```


## 配置管理员账号
### 导入密钥
```sh
cleos wallet import --private-key 5JRM3h5y6nWZxYwvGjKNjKAPxT2Jc22QnidLcoms6P3vw4BNqbf
cleos wallet import --private-key 5KSzVdujy6J31ALfULwAAAnaoj8H377eURv39s8VQ1ij4NKoBoe
cleos wallet import --private-key 5J67dbxvh9rKuJWbGVS2ef24wtXsGH6WCx8wNLJQ68XwLpZU9bu
cleos wallet import --private-key 5HsKeJf7d6YYjDrZYt6J7ax6JP85S5bc14TBWtRWodA67CrSLWr
cleos wallet import --private-key 5JpkxcQ6dX8eSjacT9R4GwUAp7PAZyxt7xoMGEspG9ANdzddgB7
cleos wallet import --private-key 5KQ1MzBpKgZB1rX5nQ9jaUqCRGm7EV7pfFfVmFxuibsofFgafgA
cleos wallet import --private-key 5HvYbZHFyFRXd2axK4Dzm9gGP8S6cPoTZuqFS3tHgYWpAb1YFDy
cleos wallet import --private-key 5KaW3M8GKaTTsFMh5VrFNxru2YGznc4PpTCGLYd7Sz7B8j8ZSiU 
```

### 创建账户
```sh
  cleos create account eosio eosio.token EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.msig EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.ram EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.ramfee EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.stake EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.names EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.savin EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.bpay EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.vpay EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
  cleos create account eosio eosio.wrap EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu EOS6ggwSrZ4yGFKsnzESw4xzD8LsWB4YgCrqmqVh4pE5NgYrkPWvu
```
### 部署系统合约并发行token
```sh
cleos set contract eosio.token /contracts/eosio.token -p eosio.token@active
cleos push action eosio.token create '["eosio", "10000000000.0000 SYS"]' -p eosio.token@active
cleos push action eosio.token issue '["eosio", "1000000000.0000 SYS", "memo"]' -p eosio@active
cleos set contract eosio.msig /contracts/eosio.msig -p eosio.msig@active
cleos set contract eosio.wrap /contracts/eosio.wrap -p eosio.wrap@active
```

### 激活功能协议
```
curl --request POST \
    --url http://127.0.0.1:7777/v1/producer/schedule_protocol_feature_activations \
    -d '{"protocol_features_to_activate": ["0ec7e080177b2c02b278d5088611686b49d739925a92d9bfcacd7fc6b74053bd"]}'
```

### 启动协议功能
```sh
cleos set contract eosio /contracts/eosio.boot -p eosio@active

# KV_DATABASE
cleos push action eosio activate '["825ee6288fb1373eab1b5187ec2f04f6eacb39cb3a97f356a07c91622dd61d16"]' -p eosio

# ACTION_RETURN_VALUE
cleos push action eosio activate '["c3a6138c5061cf291310887c0b5c71fcaffeab90d5deb50d3b9e687cead45071"]' -p eosio

# CONFIGURABLE_WASM_LIMITS
cleos push action eosio activate '["bf61537fd21c61a60e542a5d66c3f6a78da0589336868307f94a82bccea84e88"]' -p eosio

# BLOCKCHAIN_PARAMETERS
cleos push action eosio activate '["5443fcf88330c586bc0e5f3dee10e7f63c76c00249c87fe4fbf7f38c082006b4"]' -p eosio

# GET_SENDER
cleos push action eosio activate '["f0af56d2c5a48d60a4a5b5c903edfb7db3a736a94ed589d0b797df33ff9d3e1d"]' -p eosio

# FORWARD_SETCODE
cleos push action eosio activate '["2652f5f96006294109b3dd0bbde63693f55324af452b799ee137a81a905eed25"]' -p eosio

# ONLY_BILL_FIRST_AUTHORIZER
cleos push action eosio activate '["8ba52fe7a3956c5cd3a656a3174b931d3bb2abb45578befc59f283ecd816a405"]' -p eosio

# RESTRICT_ACTION_TO_SELF
cleos push action eosio activate '["ad9e3d8f650687709fd68f4b90b41f7d825a365b02c23a636cef88ac2ac00c43"]' -p eosio

# DISALLOW_EMPTY_PRODUCER_SCHEDULE
cleos push action eosio activate '["68dcaa34c0517d19666e6b33add67351d8c5f69e999ca1e37931bc410a297428"]' -p eosio

 # FIX_LINKAUTH_RESTRICTION
cleos push action eosio activate '["e0fb64b1085cc5538970158d05a009c24e276fb94e1a0bf6a528b48fbc4ff526"]' -p eosio

 # REPLACE_DEFERRED
cleos push action eosio activate '["ef43112c6543b88db2283a2e077278c315ae2c84719a8b25f25cc88565fbea99"]' -p eosio

# NO_DUPLICATE_DEFERRED_ID
cleos push action eosio activate '["4a90c00d55454dc5b059055ca213579c6ea856967712a56017487886a4d4cc0f"]' -p eosio

# ONLY_LINK_TO_EXISTING_PERMISSION
cleos push action eosio activate '["1a99a59d87e06e09ec5b028a9cbb7749b4a5ad8819004365d02dc4379a8b7241"]' -p eosio

# RAM_RESTRICTIONS
cleos push action eosio activate '["4e7bf348da00a945489b2a681749eb56f5de00b900014e137ddae39f48f69d67"]' -p eosio

# WEBAUTHN_KEY
cleos push action eosio activate '["4fca8bd82bbd181e714e283f83e1b45d95ca5af40fb89ad3977b653c448f78c2"]' -p eosio

# WTMSIG_BLOCK_SIGNATURES
cleos push action eosio activate '["299dcb6af692324b899b39f16d5a530a33062804e41f09dc97e9f156b4476707"]' -p eosio
```

### 设置kvtable和kvmap的最大key和value
```
cleos set contract eosio /contracts/eosio.bios -p eosio@active

cleos push action eosio setkvparams '[{"max_key_size":64, "max_value_size":1024, "max_iterators":128}]' -p eosio@active
```

### 部署系统合约
```
cleos set contract eosio /contracts/eosio.system -p eosio@active
```

### 授予eosio.msig特权
```sh
  cleos push action eosio setpriv '["eosio.msig", 1]' -p eosio@active
```

### 初始化
```sh

```
### eos系统账号
系统账号包含：
```
eosio.token 发行和管理token的账户；
eosio.msig 多重签名管理的账户；
eosio.wrap  多签使用
eosio.ram 内存买卖管理的账户；
eosio.ramfee 内存买卖收取手续费的账户，按照每笔交易千分之5的费率收取手续费；
eosio.stake 管理EOS抵押的账户；
eosio.names 靓号账户拍卖管理的账户；
eosio.saving 增发EOS临时存放账户，增发总量 5%，其中80%放在此账户，另外 20%再分成25%和75%，分别给eosio.bpay和eosio.vpay；
eosio.bpay 矿工获取出块奖励的临时代管账户，增发EOS的1%的25%会先转到这个账户；
eosio.vpay 矿工按照获得投票多少比例获取奖励的临时代管账户，增发EOS的1%的75%会先转到这个账户。
```

系统合约包含：
```
eosio.token
eosio.msig 此部署后需要授予eosio.msig特权
eosio.system 最后部署，并且部署前将合约代码中的21全部修改为5（共两处；主网为21个生产节点）。
```
