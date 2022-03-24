# Source

https://developers.eos.io/welcome/latest/tutorials/bios-boot-sequence#1-create-configure-and-start-the-genesis-node

# Steps

## Create the specials account (not sure about the order of these commands in all)

cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.bpay EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.msig EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.names EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.ram EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.ramfee EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.saving EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.stake EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.token EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.vpay EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj
cleos --url=http://eos1.anthonybrochu.com:8889 create account eosio eosio.rex EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj


## Build the contracts

cleos --url=http://eos1.anthonybrochu.com:8889 set contract eosio.token /home/anthony/edev/contracts-eos/eosio-sources/eosio.contracts/build/contracts/eosio.token/

cleos --url=http://eos1.anthonybrochu.com:8889 set contract eosio.msig /home/anthony/edev/contracts-eos/eosio-sources/eosio.contracts/build/contracts/eosio.msig/

## Create the tokens

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio.token create '[ "eosio", "10000000000.0000 SYS" ]' -p eosio.token@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio.token issue '[ "eosio", "1000000000.0000 SYS", "memo" ]' -p eosio@active

## Activate Features

curl --request POST \
    --url http://eos1.anthonybrochu.com:8889/v1/producer/schedule_protocol_feature_activations \
    -d '{"protocol_features_to_activate": ["0ec7e080177b2c02b278d5088611686b49d739925a92d9bfcacd7fc6b74053bd"]}'

cleos --url=http://eos1.anthonybrochu.com:8889 set contract eosio /home/anthony/edev/contracts-eos/eosio-sources/eos/contracts/contracts/eosio.boot/build/eosio.boot/

## Activate certain optionnal featuress

### KV_DATABASE
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["825ee6288fb1373eab1b5187ec2f04f6eacb39cb3a97f356a07c91622dd61d16"]' -p eosio

### ACTION_RETURN_VALUE
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["c3a6138c5061cf291310887c0b5c71fcaffeab90d5deb50d3b9e687cead45071"]' -p eosio

### CONFIGURABLE_WASM_LIMITS
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["bf61537fd21c61a60e542a5d66c3f6a78da0589336868307f94a82bccea84e88"]' -p eosio

### BLOCKCHAIN_PARAMETERS
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["5443fcf88330c586bc0e5f3dee10e7f63c76c00249c87fe4fbf7f38c082006b4"]' -p eosio

### GET_SENDER
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["f0af56d2c5a48d60a4a5b5c903edfb7db3a736a94ed589d0b797df33ff9d3e1d"]' -p eosio

### FORWARD_SETCODE
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["2652f5f96006294109b3dd0bbde63693f55324af452b799ee137a81a905eed25"]' -p eosio

### ONLY_BILL_FIRST_AUTHORIZER
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["8ba52fe7a3956c5cd3a656a3174b931d3bb2abb45578befc59f283ecd816a405"]' -p eosio

### RESTRICT_ACTION_TO_SELF
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["ad9e3d8f650687709fd68f4b90b41f7d825a365b02c23a636cef88ac2ac00c43"]' -p eosio

### DISALLOW_EMPTY_PRODUCER_SCHEDULE
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["68dcaa34c0517d19666e6b33add67351d8c5f69e999ca1e37931bc410a297428"]' -p eosio

 ### FIX_LINKAUTH_RESTRICTION
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["e0fb64b1085cc5538970158d05a009c24e276fb94e1a0bf6a528b48fbc4ff526"]' -p eosio

 ### REPLACE_DEFERRED
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["ef43112c6543b88db2283a2e077278c315ae2c84719a8b25f25cc88565fbea99"]' -p eosio

### NO_DUPLICATE_DEFERRED_ID
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["4a90c00d55454dc5b059055ca213579c6ea856967712a56017487886a4d4cc0f"]' -p eosio

### ONLY_LINK_TO_EXISTING_PERMISSION
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["1a99a59d87e06e09ec5b028a9cbb7749b4a5ad8819004365d02dc4379a8b7241"]' -p eosio

### RAM_RESTRICTIONS
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["4e7bf348da00a945489b2a681749eb56f5de00b900014e137ddae39f48f69d67"]' -p eosio

### WEBAUTHN_KEY
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["4fca8bd82bbd181e714e283f83e1b45d95ca5af40fb89ad3977b653c448f78c2"]' -p eosio

### WTMSIG_BLOCK_SIGNATURES
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio activate '["299dcb6af692324b899b39f16d5a530a33062804e41f09dc97e9f156b4476707"]' -p eosio


## Deploy other utility Contract

cleos --url=http://eos1.anthonybrochu.com:8889 set contract eosio /home/anthony/edev/contracts-eos/eosio-sources/eosio.contracts/build/contracts/eosio.system/

## Create a new producer

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio setpriv '["eosio.msig", 1]' -p eosio@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio init '["0", "4,SYS"]' -p eosio@active


cleos --url=http://eos1.anthonybrochu.com:8889 system newaccount eosio --transfer accountnum11 EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj --stake-net "100000000.0000 SYS" --stake-cpu "100000000.0000 SYS" --buy-ram-kbytes 8192

cleos --url=http://eos1.anthonybrochu.com:8889 system regproducer accountnum11 EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj https://accountnum11.com EOS84kMbo8nunhUpT8WrMpAt9BNyY1criza9CvqXXaYDLPHg18Ejj

cleos --url=http://eos1.anthonybrochu.com:8889 system listproducers

cleos --url=http://eos1.anthonybrochu.com:8889 system voteproducer prods accountnum11 accountnum11

## Resign other accounts

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio.prods", "permission": "active"}}]}}' -p eosio@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio.prods", "permission": "active"}}]}}' -p eosio@active


cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.bpay", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.bpay@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.bpay", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.bpay@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.msig", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.msig@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.msig", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.msig@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.names", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.names@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.names", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.names@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.ram", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.ram@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.ram", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.ram@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.ramfee", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.ramfee@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.ramfee", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.ramfee@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.saving", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.saving@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.saving", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.saving@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.stake", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.stake@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.stake", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.stake@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.token", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.token@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.token", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.token@active

cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.vpay", "permission": "owner", "parent": "", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.vpay@owner
cleos --url=http://eos1.anthonybrochu.com:8889 push action eosio updateauth '{"account": "eosio.vpay", "permission": "active", "parent": "owner", "auth": {"threshold": 1, "keys": [], "waits": [], "accounts": [{"weight": 1, "permission": {"actor": "eosio", "permission": "active"}}]}}' -p eosio.vpay@active
